---
title: "HOWTO: Installing KTorrent – KDE-based torrent client"
date: 2005-06-19
forum: Outdated Tutorials &amp; Tips
---

### Post by SGC on 2005-06-19
**KTorrent is a new bittorrent client for KDE. It's has the following feature:** 
-	Downloads torrent files
-	Upload speed capping,
-	Web-based bittorent search engine
-	Support for UDP Trackers.

[Screenshots of the program](http://ktorrent.pwsp.net/pics.php) 

**Install checkinstall:**
sudo apt-get install checkinstall

**Download the source package:**
wget [http://ktorrent.pwsp.net/downloads/ktorrent-1.0.tar.gz](http://ktorrent.pwsp.net/downloads/ktorrent-1.0.tar.gz)

**Extract the archive:**
tar -xvzf ktorrent-1.0.tar.gz  

**Navigate to the extracted folder:**
cd ktorrent-1.0

**Configure the package, using this command:**
./configure

**Or this (for faster compilation):**
./configure --enable-final

**Note: if you does not compile a KDE based package before, you will get an error message complaining about missing KDE/QT headers or libraries files. To fix this problem, install the following packages:**
sudo apt-get install libqt3-mt-dev kdelibs4-dev

**Compile the package:**
make

**Install the package:**
sudo checkinstall -D make install

**You will find the program in the following place:**
Kmenu > Internet > Bittorent Client (KTorrent)

---

### Post by Flawed on 2005-06-25
Hi, sounds good, but I can't "make" your source. Here's the error message I get:

```
tomake-1.9 --gnu
 cd . && perl admin/am_edit
Can't open perl script "admin/am_edit": No such file or directory
make: *** [Makefile.in] Error 1
```

I can't find a file called "am_edit" anywhere.

---

### Post by 8FootSativa on 2005-06-25
Thanks for the guide. I just wish it was stable on my system.

---

### Post by dabear on 2005-06-25
I haven't tried installing it yet, but why "make install"? You won't get a .deb package this way, and removing ktorrent will mos likely be a pain in the ass. Install checkinstall and do a "make checkinstall" instead of "make install"

---

### Post by ltmon on 2005-06-26
Also I think that in Kubuntu you should configure using:

> ./configure --prefix=/usr

This ensures that ktorrent is installed alongside all the other kde apps.

When using checkinstall, send it the -D flag for "Debian".

> sudo checkinstall -D make install

Cheers,

L.

---

### Post by SGC on 2005-06-26
I updated the HOWTO to includes checkinstall, Thank you for suggesting that.

---

### Post by SGC on 2005-07-12
Updated for the latest version

---

### Post by rubengs on 2005-07-29
Right now there are new repos, look (from ktorrent page): 

[http://ktorrent.pwsp.net/downloads.php](http://ktorrent.pwsp.net/downloads.php) 

"Ubuntu :

Add "deb [http://dinton.no-ip.org/](http://dinton.no-ip.org/) kubuntu main" and "deb-src [http://dinton.no-ip.org/](http://dinton.no-ip.org/) kubuntu main" to the repo list (with synaptic or manually in /etc/apt/sources.list)

Then, "apt-get update" to get the list of all packages available for all repos, and "apt-get install ktorrent" to install the application. (Thanks to Tonio)"

---

### Post by nickless on 2005-08-29
How good is ktorrent? Compared to Azureus?

---

### Post by sk545 on 2005-08-29
umm, you can't really compare any client to Azureus.  Azureus is too good, well, if you're looking for tons of options that is.

---

### Post by nickless on 2005-08-30
Hrm well azureus uses java and is said to slow everything down a lot. I don't need many options, I need a fast an clean torrent program :) I'll see what ktorrent has to offer me.

---

### Post by Gobd on 2006-06-02
How about a  guide for installing the latest version of Ktorrent (2.0b1) which looks very nice. I followed this guide and applied it to the new version and it failed with a few errors messages I don't understand.

---

### Post by psychicdragon on 2006-06-04
[QUOTE=Gobd]How about a  guide for installing the latest version of Ktorrent (2.0b1) which looks very nice. I followed this guide and applied it to the new version and it failed with a few errors messages I don't understand.[/QUOTE]
I posted a KTorrent 2.0beta1 package I built here: [http://ubuntuforums.org/showthread.php?t=188530](http://ubuntuforums.org/showthread.php?t=188530)

---

### Post by lenninct on 2007-06-28
how do i make ktorrent my prmary application for torrents?
everytime i try to download a file i have to save the torrent and then open it up from ktorrent.

---

