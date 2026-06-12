---
title: "Minimal xfce install - MacBook virtual box"
date: 2007-11-20
forum: Outdated Tutorials &amp; Tips
---

### Post by mmtowns on 2007-11-20
Hi all,
I decided to embark on a minimal install via VirtualBox on my Macbook.  My goal was to have some fun, learn a little bit about doing an install from the "ground up" and creating a system that is quick, easily configured and for checking email. :)

This tutorial assumes you have Virtual Box installed and running...and are able to create a new virtual machine easily.  I allocated 384 ram, but that's more than really needed for my current setup.

1) Install a command line system only from the Gutsy ALTERNATE CD.

After reboot, login with your created username and password.
comment out CD source:
```

sudo nano -B /etc/apt/sources.list
```

2) Install xorg 
```
sudo aptitude install xorg
```
3) Install xfce 
```
sudo aptitude install xfce4
```
4) Install thunar file manager
```
sudo aptitude install thunar
```
5) Install synaptic
```
sudo aptitude install synaptic
```
6) Install firefox
```
sudo aptitude install firefox
```

7) Fire up your gui and enjoy!
```
startx
```

See attached screenshot.

Credits: [https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)
[http://psychocats.net/ubuntu/minimal#barebones](http://psychocats.net/ubuntu/minimal#barebones)

---

