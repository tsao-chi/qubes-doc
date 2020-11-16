---
layout: doc
title: AnBox
permalink: /doc/anbox/
---

AnBox
=====
Anbox is a container-based approach to boot a full Android system on a regular GNU/Linux system.

Install AnBox in Debian Template
---------------------------------
```
sudo apt install snapd dkms git
sudo snap set system proxy.http="http://127.0.0.1:8082/"
sudo snap set system proxy.https="http://127.0.0.1:8082/"
snap install core
https_proxy=http://127.0.0.1:8082/ git clone https://github.com/anbox/anbox-modules.git
cd anbox-modules
sudo cp anbox.conf /etc/modules-load.d/ && sudo cp 99-anbox.rules /lib/udev/rules.d/ && sudo cp -rT ashmem /usr/src/anbox-ashmem-1 && sudo cp -rT binder /usr/src/anbox-binder-1
sudo dkms install anbox-ashmem/1 && sudo dkms install anbox-binder/1
snap install --devmode --beta anbox
```
