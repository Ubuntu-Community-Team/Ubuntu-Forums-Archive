---
title: "HOWTO: Install VLC in Breezy"
date: 2005-09-21
forum: Outdated Tutorials &amp; Tips
---

### Post by 0V3RC10CK3D on 2005-09-21
I've only been using Breezy, my first distro of linux, for about a day and a half, and this is my collective knowledge thus far. LOL

###INSTALLING VIDEOLAN IN BREEZY###

*Open the terminal
sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
sudo gedit /etc/apt/sources.list

*Add the following to the bottom and save
** I'd also uncomment all the locations while you're here
** Delete the # before all the location lines.
deb [http://download.videolan.org/pub/videolan/debian](http://download.videolan.org/pub/videolan/debian) sarge main
deb-src [http://download.videolan.org/pub/videolan/debian](http://download.videolan.org/pub/videolan/debian) sarge main

*Open the terminal
sudo apt-get update
sudo apt-get install vlc

*To start vlc open the terminal and type in 
VLC
then push enter

###DVD Playback in VLC###
Go to System -> Administration -> Synaptic Package Manager
Select All on the left
navigate to libdvdpsi3 and set the following to *mark for installation*
	libdvdpsi3
	libdvdcss2 *most important
	libdvdnav4
	libdvdplay0
	libdvdread3
Click the apply button to install them all, now dvd's should run in VLC, but most likely it's choppy.

###Fix choppyness###
So to fix the choppies we need to enable DMA on the drive, I believe it makes the drive read ahead so that it has the data cached before you actually need it, thus making the video smoother by not reading it as it needs it.

*Open the terminal
sudo cp /etc/hdparm.conf /etc/hdparm.conf_backup
sudo gedit /etc/hdparm.conf
* Add the following to the bottom and save.

/dev/dvd {
dma = on 
}

Now VLC should work in Breezy and play dvd's smoothy, yay!

###Change DVD startup to VLC### *Thanks to matthew*
Go to System -> Preferences -> Removeable Drives and Media
Click on the Multimedia tab
Under Video DVD Discs change the Command to
vlc dvd://

Done ^^

---

### Post by rwabel on 2005-09-22
[QUOTE=0V3RC10CK3D]I've only been using Breezy, my first distro of linux, for about a day and a half, and this is my collective knowledge thus far. LOL

###INSTALLING VIDEOLAN IN BREEZY###

*Open the terminal
sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
sudo gedit /etc/apt/sources.list

*Add the following to the bottom and save
** I'd also uncomment all the locations while you're here
** Delete the # before all the location lines.
deb [http://download.videolan.org/pub/videolan/debian](http://download.videolan.org/pub/videolan/debian) sarge main
deb-src [http://download.videolan.org/pub/videolan/debian](http://download.videolan.org/pub/videolan/debian) sarge main

*Open the terminal
sudo apt-get update
sudo apt-get install vlc

*To start vlc open the terminal and type in 
VLC
then push enter

###DVD Playback in VLC###
Go to System -> Administration -> Synaptic Package Manager
Select All on the left
navigate to libdvdpsi3 and set the following to *mark for installation*
	libdvdpsi3
	libdvdcss2 *most important
	libdvdnav4
	libdvdplay0
	libdvdread3
Click the apply button to install them all, now dvd's should run in VLC, but most likely it's choppy.

###Fix choppyness###
So to fix the choppies we need to enable DMA on the drive, I believe it makes the drive read ahead so that it has the data cached before you actually need it, thus making the video smoother by not reading it as it needs it.

*Open the terminal
sudo cp /etc/hdparm.conf /etc/hdparm.conf_backup
sudo gedit /etc/hdparm.conf
* Add the following to the bottom and save.

/dev/dvd {
dma = on 
}

Now VLC should work in Breezy and play dvd's smoothy, yay!

###Change DVD startup to VLC### *Thanks to matthew*
Go to System -> Preferences -> Removeable Drives and Media
Click on the Multimedia tab
Under Video DVD Discs change the Command to
vlc dvd://

Done ^^[/QUOTE]
 why adding that repository? breezy has version 0.8.2, no need for adding another repository :-)

---

### Post by 0V3RC10CK3D on 2005-09-22
[QUOTE=rwabel]why adding that repository? breezy has version 0.8.2, no need for adding another repository :-)[/QUOTE]

[QUOTE=0V3RC10CK3D]I've only been using Breezy, my first distro of linux, for about a day and a half[/QUOTE]



........oops?

---

### Post by thechitowncubs on 2005-09-22
wow  :neutral:

---

### Post by rwabel on 2005-09-23
[QUOTE=0V3RC10CK3D]........oops?[/QUOTE]
 ;-)
also try to check in ubuntu repository. They have 97% of the packages you'll ever need :-)
it's also much more comfortable.

---

### Post by GoA on 2005-09-23
What a? VLC plays dvd's for me without that tuning... And using Breezy.

---

### Post by 0V3RC10CK3D on 2005-09-23
[QUOTE=GoA]What a? VLC plays dvd's for me without that tuning... And using Breezy.[/QUOTE]

Wouldn't for me, maybe you installed the libraries prior to VLC?

---

### Post by geekman on 2005-09-26
hi i am a reel n00b with linux, i am just starting to learn to install stuff, anyways...
firstly i dloaded a new copy of vlc and ran configure, then it says it cant find MAD, but MAD wont install when i try either. Then i came across this post but i dont think it is working heres what happens (also im running ubuntu 5.04):
geekman@ubuntu:~$ sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
geekman@ubuntu:~$ sudo gedit /etc/apt/sources.list
geekman@ubuntu:~$ sudo apt-get update
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security Release.gpg [189B]
Get:2 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hoary Release.gpg [189B]
Get:3 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hoary-updates Release.gpg [189B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security Release
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hoary Release
Ign [http://download.videolan.org](http://download.videolan.org) sarge Release.gpg
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hoary-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/restricted Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hoary/main Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hoary/restricted Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hoary/main Sources
Ign [http://download.videolan.org](http://download.videolan.org) sarge Release
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hoary/restricted Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hoary-updates/main Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hoary-updates/restricted Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hoary-updates/main Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hoary-updates/restricted Sources
Ign [http://download.videolan.org](http://download.videolan.org) sarge/main Packages
Ign [http://download.videolan.org](http://download.videolan.org) sarge/main Sources
Get:4 [http://download.videolan.org](http://download.videolan.org) sarge/main Packages [20B]
Get:5 [http://download.videolan.org](http://download.videolan.org) sarge/main Sources [20B]
Fetched 43B in 4s (10B/s)
Reading package lists... Done
geekman@ubuntu:~$ sudo apt-get install vlc
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package vlc
PLEASE HELP!!!!!
thnx in Adv:confused:

---

### Post by coaxx on 2005-11-20
[QUOTE=rwabel]why adding that repository? breezy has version 0.8.2, no need for adding another repository :-)[/QUOTE]


Oh can you post your sources.list please? My Breezy does not find vlc :(

---

### Post by rwabel on 2005-11-20
[quote=coaxx]Oh can you post your sources.list please? My Breezy does not find vlc :([/quote]

sure, you need to enable the universe repository:
```
deb http://security.ubuntu.com/ubuntu breezy-security universe
```

---

### Post by unf on 2005-12-20
> deb [http://download.videolan.org/pub/videolan/debian](http://download.videolan.org/pub/videolan/debian) sarge main
deb-src [http://download.videolan.org/pub/videolan/debian](http://download.videolan.org/pub/videolan/debian) sarge main

*Open the terminal
sudo apt-get update
sudo apt-get install vlc
This is not working....

sudo apt-get install vlc > package is missing blaa blaa blaa.Yes I did sudo apt-get update.

---

### Post by decaf on 2006-01-19
I recompiled Dapper's Videolan (with Gtk2) for Breezy, without ".mkv" (matroska) support . Add this line to your sources.list:

deb [http://dot.name.tr/ubuntu-decaf/](http://dot.name.tr/ubuntu-decaf/) debs/

These are other lines you need for all Breezy systems:

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy-backports main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy-updates main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy-security main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted universe multiverse

---

### Post by Noremacam on 2006-01-19
[QUOTE=0V3RC10CK3D]
###Fix choppyness###
So to fix the choppies we need to enable DMA on the drive, I believe it makes the drive read ahead so that it has the data cached before you actually need it, thus making the video smoother by not reading it as it needs it.
[/QUOTE]

Actually, DMA stands for Direct Memory Access. Plainly speaking, the data goes straight from the drive to memory, without going through the cpu and wasting cpu cycles. That's why you get the big performance boost with DMA activated.

---

