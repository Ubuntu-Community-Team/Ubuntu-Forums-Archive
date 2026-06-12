---
title: "Slim Edgy setup from mini.iso"
date: 2006-11-14
forum: Outdated Tutorials &amp; Tips
---

### Post by druhboruch on 2006-11-14
This is my first how-to.  It is for users who wish to run slim edgy setup.

First download mini.iso and burn to the CD.

Boot your PC and perform server installation 

```
server
```

After rebooting login to your fresh server installation and update sources.list

```
sudo nano -w /etc/apt/sources.list
```

Add universe and multiverse repositories.

```
sudo apt-get update
sudo apt-get dist-upgrade

```

Now let us install xorg

```
sudo apt-get install xserver-xorg-video-vesa
```

Instead of vesa you can install xorg driver for your vga.

```
sudo apt-get install xorg
```

Now let us install gnome and gdm

```
sudo apt-get install gnome-core gdm
```

Usplash and artwork are optional but desirable

```
sudo apt-get install usplash usplash-theme-ubuntu
sudo apt-get install ubuntu-artwork
```

This is it.










Links:
[ftp://ftp.osuosl.org/pub/ubuntu/dists/edgy/main/installer-i386/current/images/netboot](ftp://ftp.osuosl.org/pub/ubuntu/dists/edgy/main/installer-i386/current/images/netboot)
[http://www.howtoforge.com/perfect_setup_ubuntu_6.10](http://www.howtoforge.com/perfect_setup_ubuntu_6.10)

---

### Post by wykedengel on 2006-12-12
First, thanks for a wonderful tut. I learned more about Ubuntu through this tutorial, than on trying to Google information on my own. I tested this unstall using Edgy on the following:

IBM Thinkpad model T22
PIII 900MHz 160mb ram
80G HD, DVD/CD+RW

The installation was painless to say the least. I can safely say that it was easier going this route that using the alt install cd. Before doing any tweaks, I have to say that laptop is out performing my desktop (similar processor--though the desktop has 512mb ram).

I am going to take my time and install only what i need. While having all the bells and whistles are nice, I am happy with the system I created with this tut.

---

