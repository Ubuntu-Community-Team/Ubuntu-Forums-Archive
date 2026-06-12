---
title: "How can I run USB Creator etc in Linux which I originally downloaded in Windows?"
date: 2012-01-31
forum: New to Ubuntu
---

### Post by davidc60 on 2012-01-31
Hi,  
  I am presently running Ubuntu 11.10 (from a USB) as the Administrator. I have a number  of programs like Unetbootin, USB Creator and USB Universal Installer (as well as various Linux-related ISO's) on another USB which I copied and pasted there from Windows where I originally downloaded them. When I copy/paste them into Ubuntu (and other Linux distros) and then try to run them in order to install the ISO's to another USB or the HDD I get messages from Mono Runtime and/or the Archive Manager effectively saying that I cannot open those programs ie.
 [INDENT]***Archive:  /media/mint/home/david/Documents/USB CREATOR/MAIN LILI EXE FILE FILE/LinuxLive USB Creator 2.8.8.exe *** 
***[/media/mint/home/david/Documents/USB CREATOR/MAIN LILI EXE FILE FILE/LinuxLive USB Creator 2.8.8.exe] *** 
  ***End-of-central-directory signature not found.  Either this file is not *** 
  ***a zipfile, or it constitutes one disk of a multi-part archive.  In the *** 
  ***latter case the central directory and zipfile comment will be found on *** 
  ***the last disk(s) of this archive. *** 
***note:  /media/mint/home/david/Documents/USB CREATOR/MAIN LILI EXE FILE FILE/LinuxLive USB Creator 2.8.8.exe may be a plain executable, not an archive *** 
***zipinfo:  cannot find zipfile directory in one of /media/mint/home/david/Documents/USB CREATOR/MAIN LILI EXE FILE FILE/LinuxLive USB Creator 2.8.8.exe or *** 
***/media/mint/home/david/Documents/USB CREATOR/MAIN LILI EXE FILE FILE/LinuxLive USB Creator 2.8.8.exe.zip, and cannot find /media/mint/home/david/Documents/USB CREATOR/MAIN LILI EXE FILE FILE/LinuxLive USB Creator 2.8.8.exe.ZIP, period. ***[/INDENT]                   
 Can anyone please enlighten me as to what it is with Ubuntu that is preventing me from using these Installers and ISO's – I really don't want to have to download all of them again. Is there something in Ubuntu etc. that I need to download/amend to enable me to be able to make use of the existing installer programs and the ISO's?  Thanks,
 davidc

---

### Post by rgreener25 on 2012-01-31
You can use unetbootin on linux just type ```
sudo apt-get install unetbootin
``` then run it from the menu and you can make ubuntu ones by using startup disk creater (pre-installed)

---

### Post by satanselbow on 2012-01-31
This is spam right?

---

### Post by arpanaut on 2012-01-31
You cannot run .exe files in Linux those are Windows execuitable files, they are not compatible with Linux.

---

### Post by C.S.Cameron on 2012-02-01
Startup Disk creator is the Linux version of usb-creator.exe.
Click Dash and type "st".

---

### Post by davidc60 on 2012-02-01
Thanks for your helpful replies.
davidc

---

