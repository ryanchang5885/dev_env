# UrDev Docker Compose

#### Easy joint development via Docker and Docker Compose

## Starting a new project

Make sure you have the latest versions of **Docker** and **Docker Compose** installed on your machine.
Get the **docker-compose.yml** file from this repository into a blank folder.

##### Create containers
Get ready for virutal machine or machine
* Recommend OS: "Ubuntu 18.04 LTS"
* Enable SSH with screen for development

```
sudo apt-get update
sudo apt install docker.io
sudo apt install docker.compose
```
Get **docker-compose.yml** file from this repository 

```
mkdir urdev && cd urdev
git clone https://github.com/ryanchang5885/dev_env.git
sudo docker-compose up
```
Okay to go

```
sudo docker-compose up
```
This create 2 new folders beside your docker-compose.yml file.
* **wp-app** - the location of your Wordpress application
* **wp-data** - used to store and restore database dumps

The containers are now build and running. 
You should be able to access the Wordpress installation with the configured IP in the browser address. For convenience you may add a new entry into your hosts file.

##### Quick Start
* Starting containers
```
sudo docker-compose start
```
* Stopping containers
```
sudo docker-compose stop
```
* Remove containers
```
sudo docker-compose down
```
... or the **rm** command if the containers are stopped already.
```
sudo docker-compose rm
```

## Project from existing source

Copy the docker-compose.yml file into a new directory. In the directory you create two folders:
* **wp-data** - here you add the database dump
* **wp-app** - here you copy your existing wordpress code

You can now use the **up** command:
```
sudo docker-compose up
```

This will create the containers and populate the database with the given dump. You may set your host entry and change it in the database, or you simply overwrite it in the **wp-config.php** by adding
```
define('WP_HOME','http://wp-app.local');
define('WP_SITEURL','http://wp-app.local');
```

## Creating database dumps
```
sudo ./export.sh
```
---

## Misc
* Developing a Theme
Configure the volume to load the theme in the container in the docker-compose.yml

```
volumes:
  - ./theme-name/trunk/:/var/www/html/wp-content/themes/theme-name
```
* Developing a Plugin

Configure the volume to load the plugin in the container in the docker-compose.yml

```
volumes:
  - ./plugin-name/trunk/:/var/www/html/wp-content/plugins/plugin-name
```
