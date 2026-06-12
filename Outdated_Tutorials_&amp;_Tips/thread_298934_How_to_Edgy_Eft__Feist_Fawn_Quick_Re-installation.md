---
title: "How to: Edgy Eft / Feist Fawn Quick Re-installation"
date: 2006-11-13
forum: Outdated Tutorials &amp; Tips
---

### Post by TheeMahn2003 on 2006-11-13
I would like to share a number of scripts I have written to get Edgy Eft or Feisty Fawn up and running with newer then the repos or automatix offer applications and drivers.  This does require some work on your behalf and a partition or additional hard disk.  This how to will save you a ton of time when it comes to re-installation.

What this will do as it sits all aspects are modifiable via editing the goodies.sh file in order:

[LIST]
[*]Restore your cache - reduction in downloading a great increase in speed.
[*]Install Build tools
[*]Update Software
[*]Dist-Upgrade
[*]Install Essential Software
[*]Install Nautilus Scripts
[*]Build & Install Newest Gaim
[*]Build & Install Newest Nvidia driver
[*]Build and install newest Beryl
[*]Start X
[/LIST]

**_Preparation Before Installation_**

1. Create the following structure on a partition or drive in my case I have a 320 Gig drive at /media/Storage and will base this code as such please change it accordingly to your structure.
```
cd /media/Storage
sudo mkdir Speed
sudo chmod 777 -R Speed
cd Speed
sudo mkdir Cache2
cd /var/cache/apt/archives
sudo cp *.deb /media/Storage/Speed/Cache2
```

Ok what we have accomplished so far is to backup the debs you have downloaded I have 1400+ of them from installing this or that only time you should have to download a deb again is if it's something you have not installed before or a newer version has hit the repos a real time saver when seen in action you will thank me.

2. Download all my scripts and place them in the folder Speed you have created, and extract them.

3. Make them executable
```
cd /media/Storage/Speed
sudo chmod 777 *.sh
cd Nautilus
sudo chmod 777 *

```

4. Copy your current /etc/X11/xorg.conf to this folder
```
sudo cp /etc/X11/xorg.conf /media/Storage/Speed
```

**_Install Edgy as you usually would do_**
After installation at the login screen press ctrl alt F2 and login.
goto your Speed directory and enjoy.
```
cd /media/Storage/Speed
sudo sh goodies.sh
```

Any feedback good or bad is appreciated.

Enjoy!!!

---

