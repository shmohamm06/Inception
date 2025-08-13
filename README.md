# Inception

## Overview
Inception is a Docker-based infrastructure project that sets up a complete web development environment with WordPress, Nginx, and MariaDB. This project demonstrates containerization, orchestration, and infrastructure as code principles using Docker Compose.

## Features
- **WordPress Application**: Full-featured content management system
- **Nginx Web Server**: High-performance reverse proxy and web server
- **MariaDB Database**: Reliable database management system
- **SSL/TLS Support**: Secure HTTPS connections
- **Volume Management**: Persistent data storage
- **Network Isolation**: Secure container networking
- **Environment Configuration**: Flexible configuration management

## Architecture
The project implements a three-tier architecture:
1. **Nginx**: Frontend reverse proxy with SSL termination
2. **WordPress**: Application layer with PHP-FPM
3. **MariaDB**: Database layer for data persistence

## Services

### Nginx
- **Role**: Reverse proxy and web server
- **Port**: 443 (HTTPS)
- **SSL**: Self-signed certificates
- **Configuration**: Custom nginx.conf
- **Volumes**: WordPress files and SSL certificates

### WordPress
- **Role**: Web application
- **Dependencies**: MariaDB database
- **Configuration**: Environment-based setup
- **Volumes**: Application files and uploads
- **Features**: Full CMS functionality

### MariaDB
- **Role**: Database server
- **Port**: 3306
- **Data**: Persistent storage
- **Users**: WordPress database access
- **Security**: Isolated network access

## Project Structure
```
Inception/
├── srcs/                    # Source code directory
│   ├── docker-compose.yml   # Service orchestration
│   ├── requirements/         # Service requirements
│   │   ├── nginx/          # Nginx configuration
│   │   ├── wordpress/      # WordPress setup
│   │   └── mariadb/        # MariaDB setup
│   └── .env                # Environment variables
├── Makefile                 # Build and management commands
└── .git/                   # Git repository
```

## Environment Variables
The `.env` file contains:
- `DB_NAME`: WordPress database name
- `DB_USER`: WordPress database user
- `DB_PASS`: WordPress database password
- `DB_ROOT`: MariaDB root password

## Usage

### Starting the Infrastructure
```bash
# Launch all services
make

# Build and launch (if changes made)
make build

# Stop all services
make down

# Rebuild everything
make re
```

### Management Commands
```bash
# View running containers
docker ps

# View logs
docker-compose -f srcs/docker-compose.yml logs

# Access WordPress
# Open https://localhost in your browser

# Access MariaDB
docker exec -it mariadb mysql -u root -p
```



## Requirements
- Docker
- Docker Compose
- Make utility
- Sufficient disk space for volumes
- Port 443 available

## Data Persistence
- **WordPress Data**: Stored in `~/data/wordpress/`
- **Database Data**: Stored in `~/data/mariadb/`
- **SSL Certificates**: Stored in nginx container
- **Configuration Files**: Mounted from host

## Security Features
- **Network Isolation**: Services communicate through internal network
- **SSL/TLS**: Encrypted HTTPS connections
- **User Isolation**: Separate database users
- **Volume Security**: Host-based volume mounting
- **Container Security**: Minimal attack surface

## Monitoring and Maintenance
- **Container Health**: Docker health checks
- **Log Management**: Centralized logging
- **Backup Strategy**: Volume-based data backup
- **Update Process**: Image-based updates
- **Resource Monitoring**: Docker stats

## Notes
- Follows Docker best practices
- Implements infrastructure as code
- Provides production-ready setup
- Includes comprehensive documentation
- Supports easy scaling and modification

## Author
shmohamm - 42 Abu Dhabi
