---
title: "How to : Get Kubuntu running on an acer aspire 64 bit laptop"
date: 2005-12-20
forum: Outdated Tutorials &amp; Tips
---

### Post by peanut butter on 2005-12-20
(requires internet connection)
I. Get the cds

1 download the i386 (not IA64) ubuntu (not kubuntu) cd
2 burn the image to a cd with burn cdcc or other program
3 download the kubuntu i386 cd
4 burn it

II.install

1 instal the Ubuntu Breezy disc (warning!!!!! you must have your computer connected to the internet) with the options thatyou want (to a certan extent and do let it install gnome) 
2 boot into gnome with the username and password you made at installation
3 enable the correct

III. setting up wireless card (why you use gnome first)

1 get automatix from here and select the laptop wifi option or 

install the packages ndisgtk, and ndiswrapper-utils with the commands
```

sudo apt-get -install ndiswrapper-utils
sudo apt-get -install ndisgtk

```
2 download your windows wifi driver from 
```
ftp://ftp.support.acer-euro.com/notebook/aspire_<model#>/driver/80211g.zip
```
(make shur to change <model #> to your model number
3 after it is downloaded click on it
4 tell the program to extract all the files to your home directory and to keep file structure
5 open system>administration tools>windows wireless drivers
6 type in your password to continue
7 click "install new driver"
8 click on the folder icon
9 click on 80211g
10 click on winxp
11 now doubble click on the inf file
12 click install
13 next look at where it says "hardware present:"and make sure it says "yes"
14 now click "configure network"
15 highlight wireless connection and press properties
16 configure your wireless network
17 now press "ok", "ok", "close" (in the different boxes)

IV. install KDE

if you have downloaded the kubuntu cd (if you havent ignore this) ,before you do anything go to terminal and type
```

sudo apt-cdrom add

```
insert the cd if you haven't alredy done so

press enter and wait until it says
```

(you)@(yourcomputer):~$
close the window

```

1 go to snaptic by going to system>administration>snaptic package manager
2 tipe in your password and click ok
3 at the top click the reload button,and wait,  then the search button
4 type kubuntu-desktop and click ok
5 next click on the box next to kubuntu-desktop, and on the dropdown click mark for installation
6 get a cup of tea and some cookies because this could take a while (especially if you are downloading the packages) it may ask you
7 it will ask you whether you want to use kdm or gdm select kdm
8 now restart the computer and login to KDE (wahoo!!!!!!)

you now have a fully functional kubuntu laptop!!!!!!!!;) ;) ;) :) :) :)

---

