---
title: "GT520M Nvidia Driver update fail. Only 640x480!"
date: 2013-06-23
forum: New to Ubuntu
---

### Post by Powerkiddie on 2013-06-23
Hi everyone,

First, let me start by sketching the situation.
I have upgraded my old MSI CX640 with a Geforce GT520M to Ubuntu 12.04 LTS. Mainly because I want to learn all about UNIX enviroments. Ppl told me ubuntu is a good way to start.
I already know the basics. terminal en shizzle, root-stuff, ...

Last week I tried to install the Nvidia-Driver because I want to start experimenting with Compiz and it won't work (Cube, effects, ...) with the drivers provided with the install.
So after seeking the mighty interwebs I finally found how to do install.
The command order I followed is the next:
```
[COLOR=#111111][FONT=Georgia]sudo apt-get update && sudo apt-get upgrade
sudo apt-get install linux-headers-$(uname -r)
[/FONT][/COLOR][COLOR=#111111][FONT=Georgia]
sudo chmod +x NVIDIA-Linux-x86-270.41.06.run
[/FONT][/COLOR][COLOR=#111111][FONT=Georgia]sudo gedit /etc/modprobe.d/blacklist.conf
[/FONT][/COLOR]
```
In blacklist.conf I had to add the lines:
```
[COLOR=#111111][FONT=Georgia]blacklist nouveau 
options nouveau modeset=0

[/FONT][/COLOR]
```After that step I saved and rebooted
Next:
```
[COLOR=#111111][FONT=Georgia]sudo apt-get remove --purge nvidia*
[/FONT][/COLOR][COLOR=#111111][FONT=Georgia]sudo service lightdm stop 
[/FONT][/COLOR]
```[COLOR=#111111][FONT=Georgia]
[/FONT][/COLOR]Then I did ctrl+alf+F1 >
```
[COLOR=#111111][FONT=Georgia]sudo sh ./NVIDIA-Linux-x86-270.41.06.run 
[/FONT][/COLOR]
```
And reboot.
Driver got installed successfully, but I only have a resolution of 640*480.
I don't know why. Without the driver I had a lot more. But as I said, I want those compiz-effects.
I googled it for a few days, but nothing helped.
So I hope I can find an aswer here.

Thanks in advance!

---

