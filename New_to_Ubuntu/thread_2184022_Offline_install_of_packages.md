---
title: "Offline install of packages"
date: 2013-10-27
forum: New to Ubuntu
---

### Post by reto2 on 2013-10-27
Hi, 

I'm trying to build an offline machine. After the initial install, how do I install packages? It looks like apt-offline would do the trick, however it is not included in Lubuntu 13.04.

I also looked at apt-medium, but could not figure it out. 

Is there an easy way, i.e. via an USB stick?

---

### Post by arochester on 2013-10-27
You can later add new applications using:
Keryx Project - [https://launchpad.net/keryxproject](https://launchpad.net/keryxproject)
Sushi-Huh? - [http://sushi-huh.sourceforge.net/](http://sushi-huh.sourceforge.net/)
APTonCD - [http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)
Synaptic - [http://community.linuxmint.com/tutorial/view/1059](http://community.linuxmint.com/tutorial/view/1059)

---

### Post by ian-weisser on 2013-10-27
See [https://help.ubuntu.com/community/AptGet/Offline](https://help.ubuntu.com/community/AptGet/Offline)
The Synaptic application also has a handy set of offline tools.

> **reto2 said:**
> It looks like apt-offline would do the trick, however it is not included in Lubuntu 13.04.

What's the problem?
Download the apt-offline deb from [http://packages.ubuntu.com](http://packages.ubuntu.com), USB-stick it over to your machine, and install it.

Using, for example, Ubuntu 13.10 that would be:
1) Download [http://packages.ubuntu.com/saucy/all/apt-offline/download](http://packages.ubuntu.com/saucy/all/apt-offline/download) to a USB stick
The downloaded file will be apt-offline_1.3.1_all.deb
2) Mount the USB stick in your Ubuntu system
3) Use the command **sudo dpkg --install /media/my_usb_stick/apt-offline_1.3.1_all.deb** to install the software
4) See **man apt-offline** for usage information after install.

In the specific case of apt-offline, all dependencies are included in the installed version of Ubuntu.


> **reto2 said:**
> Is there an easy way, i.e. via an USB stick? 
Yes, several: apt-offline, apt-zip, and synaptic all have good offline tools.


You will need to learn a bit about package management, else the process of installing and updating will confuse. It's not difficult.

---

