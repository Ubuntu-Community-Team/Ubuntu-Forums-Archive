---
title: "hey, there is something wrong!"
date: 2005-01-15
forum: Repositories &amp; Backports
---

### Post by madzzoni on 2005-01-15
There is some wrong with the ubuntu-Repo's.... it's not possible to install gstreamer, xmms and a lot of dependencies.... 

Please do something about this.... or should i change my source.list to debian-mirrors?

Or what????

---

### Post by Quest-Master on 2005-01-15
Replace your /etc/apt/sources.list with this.

> deb cdrom:[Ubuntu 4.10 _Warty Warthog_ - Preview i386 Binary-1 (20041020)]/ unstable main restricted 


## Uncomment the following two lines to fetch updated software from the network
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty universe

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) warty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) warty-security main restricted

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty multiverse

deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) stable main
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) unstable main
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) testing main

Then, in the terminal, do: sudo apt-get update.

---

### Post by madzzoni on 2005-01-16
Thank you!, that helps... I now using this list instead of the one from ubuntuguide.org

Cool, now it's time to install all the goodies :-)

---

### Post by Rancoras on 2005-01-16
Unless my eyes are going kaput, that is the one from ubuntuguide.  I bet you inadvertantly removed the line for the CD.  If you look carefully in the guide instructions it says replace the listed "section" with the listed lines.  It doesn't intend for you to remove the line for the CD.  The guide even gives a sample of how the file should look after editing.

---

