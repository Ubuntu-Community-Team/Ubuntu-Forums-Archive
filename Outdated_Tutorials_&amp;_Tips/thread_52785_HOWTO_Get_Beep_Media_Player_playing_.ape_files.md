---
title: "HOWTO: Get Beep Media Player playing .ape files"
date: 2005-07-28
forum: Outdated Tutorials &amp; Tips
---

### Post by GrammatonCleric on 2005-07-28
HOWTO: Get Beep Media Player playing .ape files

Introduction
-------------------------------

A friend ripped several cd's that he had and I wanted. I asked if he could rip them to OGG....Well got them in .ape.  This started my search on how to play them under linux.

******************************************
REQUIREMENTS to build the sources are:
******************************************


beep-media-player
beep-extra-plugins
beep-media-player-dev
nasm
libgtk+2.0
libglib2.0-dev



##################################################
Installing requiements:
##################################################

sudo apt-get install beep-media-player
sudo apt-get install beep-extra-plugins
sudo apt-get install beep-media-player-dev
sudo apt-get install nasm
sudo apt-get install libgtk+2.0
sudo apt-get install libglib2.0-dev

##################################################
Download the MAC libs:
##################################################


[http://prdownloads.sourceforge.net/mac-port/mac-3.99-u4-b3.tar.gz?download](http://prdownloads.sourceforge.net/mac-port/mac-3.99-u4-b3.tar.gz?download)


##################################################
Download the BMP MAC plugin:
##################################################


[http://prdownloads.sourceforge.net/mac-port/bmp-mac-0.1.1.tar.gz?download](http://prdownloads.sourceforge.net/mac-port/bmp-mac-0.1.1.tar.gz?download)

##################################################
Extract the MAC lib source:
##################################################

tar zxvf mac-3.99-u4-b3.tar.gz

##################################################
Build and install MAC lib 
##################################################


Change in to the extrect directory.
_______________________________________


cd mac-3.99-u4-b3




Configure the source.
_______________________________________


./configure





Build the binary.
_______________________________________

make


Install it.
_______________________________________

sudo make install






With the MAC libs installed it's time to build  and install the BMP plugin.




##################################################
Extract the BMP plugin:
##################################################

tar zxvf bmp-mac-0.1.1.tar.gz

##################################################
Build and install BMP plugin
##################################################


Change in to the extrect directory.
_______________________________________


cd bmp-mac-0.1.1


Configure the source.
_______________________________________


./configure


Build the binary.
_______________________________________


make


Install it.
_______________________________________

sudo make install



Launch Beep, load, play and enjoy your .ape files.

---

### Post by borland-c on 2007-11-06
it's a pity, but download pages from sourceforge.net are unavailable
is there some else source available ?

---

### Post by GrammatonCleric on 2007-11-06
Monkey Audio is available from ...

[http://morgoth.free.fr/ubports/](http://morgoth.free.fr/ubports/)

-GC

---

### Post by dveej on 2007-11-08
It was very nice of GrammatonCleric to take the trouble and time to post those detailed directions. But between the time they were posted and today (November 8), half of them don't work any more. 


Here are the parts of the instructions that don't work:

beep-extra-plugins
libgtk+2.0
MAC libs
BMP MAC plugins

And the backports at morgoth can't be downloaded either.

Any help?

Thanks.

---

### Post by GrammatonCleric on 2007-11-08
Hmmm... seems to be up and running for me...

```

Ign http://morgoth.free.fr gutsy-backports/main Packages                 
Hit http://morgoth.free.fr gutsy-backports/main Sources

``````

e$ sudo apt-get install monkeys-audio
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libmac2
The following NEW packages will be installed:
  libmac2 monkeys-audio
0 upgraded, 2 newly installed, 0 to remove and 2 not upgraded.
Need to get 79.2kB of archives.
After unpacking 238kB of additional disk space will be used.
Do you want to continue [Y/n]? 

```

I no longer use Beep-media-player.  I now use Audacious.



-GC

---

### Post by nenolod on 2007-11-16
Audacious 1.4.1 may add support for .ape files. We're not yet certain.

We do have code though.

---

