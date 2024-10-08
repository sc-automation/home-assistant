# Raspberry Pi setup (Raspberry Pi 3B)
Basic installation is done using the imager (https://www.raspberrypi.com/software/) with following values

* Raspberry Pi 3
* Raspberry Pi OS (64-bit)

Follow the instructions and enable networking/SSH. Afterwards, boot the Pi with the SD card. Find it on your network (e.g. by checking your router/DHCP server) and log in via SSH.

## after first boot
It is safe to run ```sudo apt update``` and ```sudo apt upgrade``` to update the system to the latest version and security patches.

# Home Assistant setup (with docker compose)

Install docker: https://docs.docker.com/engine/install/debian/
Finish docker setup: https://docs.docker.com/engine/install/linux-postinstall/

Clone this repository and run ```docker compose up -d``` in the main directory. Navigate to http://homeassistant.local:8123/ and complete the onboarding process.

> [!IMPORTANT]
> I opted to disable the ```privileged: true``` option in the homeassistant service. It is really not needed except for some special circumstances (and inexperienced users). But it creates a lot of trouble when you want to update and backup your configuration with Git, since the whole ```config``` directory will be owned by root. This promotes bad behaviour (doing common development tasks as root) and you should never do this.

You should now have a basic Home Assistant setup running.

## Install HACS

Follow instructions on https://www.hacs.xyz/docs/use/download/download/ and https://www.hacs.xyz/docs/use/configuration/basic/