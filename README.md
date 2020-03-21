
# Jupyter Notebook on Docker

This repository contains a Jupyter Notebook setup that assumes you have [nginx-proxy](https://github.com/nginx-proxy/nginx-proxy) and [letsencrypt-nginx-proxy-companion](https://github.com/nginx-proxy/docker-letsencrypt-nginx-proxy-companion) running.

## Prerequisites

This setup uses docker-compose and assumes you have nginx-proxy and letsencrypt-nginx-proxy-companion running. In addition, you must

- register a public domain for your Jupyter Notebook. I personally use https://duckdns.org but there are many other options out here.
- Finally, you must adjust the volume, domain/host and network name in the `docker-compose.yml` file to match your setup.

## Install

Build and run the Jupyter Notebook container by executing the following command:

``` bash
$ docker-compose up -d --build
```
Finally, confirm that you can access your Notebook at `jupyter.yourdomain.org`.

## Configuration (optional)

You may want to protect your Notebook using a password. To do this, enter your the Docker container by executing the following command (change `jupyter_jupyter_1` to match the name of your container):

``` bash
$ docker exec -it jupyter_jupyter_1 bash
```

Next, run the following command and enter a password:

``` bash
$ jupyter notebook password
```

Finally, restart your Notebook:

``` bash
$ docker-compose down
$ docker-compose up -d
```

That's it! Now you can start using your Notebook.
