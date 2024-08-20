# Downloading Setup

## Table of Contents
- [Description](#description)
- [Services Overview](#services-overview)
- [Installation](#installation)
  - [Install Docker](#install-docker)
  - [Download & Run Containers](#download--run-containers)
  - [Configuration](#configuration)
    - [Prowlarr Setup](#prowlarr-setup)
    - [Flaresolverr Integration](#flaresolverr-integration)
    - [Radarr & Sonarr Integration](#radarr--sonarr-integration)
    - [Transmission Configuration](#transmission-integration)
- [Accessing the Services](#accessing-the-services)

## Description
This setup is designed to manage torrent downloads efficiently. With it, you can easily search and download your movies or series from various torrent sources using a combination of powerful tools.

## Services Overview
This setup runs using Docker containers and includes several key services:

- **Prowlarr**: Manages torrent sources as an indexer.
- **Sonarr**: Fetches TV series.
- **Radarr**: Fetches movies.
- **Flaresolverr**: Bypasses human verification on certain torrent sites (e.g., ygg.re).
- **Transmission**: The BitTorrent client that downloads the torrent files provided by Prowlarr.

## Installation

### Install Docker
#### On Windows or macOS:
Install Docker Desktop from [here](https://www.docker.com/products/docker-desktop/).

#### On Linux:
Run the following commands:
```bash
sudo apt-get update
sudo apt-get install docker docker-compose-plugin
```

Once installed, you should be able to use `docker-compose`. Verify it by running:

### Download & run containers
Run the following command to start the containers:
```
sudo docker-compose up -d
```

### Configuration
#### Prowlarr setup

- Access to [Prowlarr](http://localhost:9696)
- Select Indexers on the left sidebar
- Click on 'Add Indexer'
- Choose all indexers you want (corresponding to torrent service(s) you use.).

#### Flaresolverr integration
- Go to Settings -> Indexers
- Click on '+' and select __Flaresolverr__. 
- Change host for `http://flaresolverr:8191/`
- Click on 'test' button and save.

#### Radarr & Sonarr Integration
- Go to Settings -> Apps from the left sidebar and click on '+' icon in Applications. 
- First, select __Radarr__.  
- Configure following fieds : 
    ```
    Name: Radarr
    Sync level: Full Sync
    Prowlarr Server: http://prowlarr:9696
    Radarr Server: http://radarr:7878
    API key: your_api_key
    ```

_To find your api key, go to [Radarr](http://radarr:7878). Go to Settings -> General and find your api key in Security section._

- Save the configuration and do the same thing for __Sonarr__ by replacing radarr by sonarr in names & urls.

_You should access to [Sonarr](http://sonarr:8989) to get the specific api key for Sonarr._

#### Transmission integration
- Go to Settings -> Download Clients then click on '+' icon and select __Transmission__. 
- Configure following fieds :
    ```
    Name: Transmission
    Enable: yes
    Host: transmisssion
    Port: 9091
    ```

Save the configuration.

### Accessing the Services
You're now ready to use services !

- [Prowlarr](http://sonarr:9696) (Indexer)
- [Radarr](http://localhost:7878) (Movies)
- [Sonarr](http://localhost:8989) (TV Series)
