---
title: "Got a problem with ATI and Ubuntu"
date: 2008-09-21
forum: New to Ubuntu
---

### Post by Vossibear on 2008-09-21
I wanted to Install my ATI HD2400 driver via Envy NG.
It worked but i had only a resolution of 640x480. That really sucked.
I uninstalled all components of Envy NG and Drivers.

Tried to install my driver manually (Tutorial wiki).
This is my installing "way":

1.sudo apt-get install build-essential debconf dh-make fakeroot gcc-3.3 libstdc++5 module-assistant 

2.sudo apt-get install dkms 

3.sudo apt-get install cdbs 

4.chmod +x ati-driver-installer-8-9-x86.x86_64.run 

5. ./ati-driver-installer-8-5-x86.x86_64.run --buildpkg Ubuntu/hardy 

6.sudo module-assistant prepare 
7.sudo module-assistant update
8.sudo module-assistant a-i fglrx
9.sudo depmod -a 



But step nr.8 does not work. 

The module asistant says **"building package fglrx-kernel-source failed"**.

What can I do next? I am really fed up with installing that driver of my ATI HD 2400 :(

HELP!!

---

### Post by markbuntu on 2008-09-21
You need to follow the directions here, Method 2:

[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)

---

