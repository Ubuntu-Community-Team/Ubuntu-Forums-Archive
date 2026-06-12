---
title: "Help with ndiswrapper"
date: 2008-08-22
forum: New to Ubuntu
---

### Post by AnonUK on 2008-08-22
Hey, I'm trying to get my Belkin wireless USB do work, and one of the steps in the process is using ndiswrapper to do certain things.

I can't access the internet on ubuntu, so i downloaded the latest version of ndiswrapper off a website (while on vista), onto a usb and tried to install it on ubuntu. This happened -


anonymous@anonymous-desktop:~$ tar zxvf ndiswrapper-1.53.tar.gz 
tar: ndiswrapper-1.53.tar.gz: Cannot open: No such file or directory 
tar: Error is not recoverable: exiting now 
tar: Child returned status 2 
tar: Error exit delayed from previous errors 

(also i tried this command as it was in the instructions)

anonymous@anonymous-desktop:~$  ls /lib/modules/`uname -r`/build 
arch    Documentation  include  Kbuild  Makefile        net      security 
block   drivers        init     kernel  mm              samples  sound 
crypto  fs             ipc      lib     Module.symvers  scripts  usr

---

### Post by kristersaurus on 2008-08-22
make sure you are in the same directory as that file. so for example, if it is on usb, you will probably need to do something like 'cd /media/usb/' from the command line before executing tar zxvf blahblah. If it is on the desktop (probably easier for you to move it there or your home directory and try it), you will need to do 'cd ~/Desktop' from the command line.

---

### Post by kristersaurus on 2008-08-22
also, it will probably be easier for you to connect your machine to the internet through a landline, run synaptic, search for ndiswrapper, and install the gui frontend for it. makes things a little easier. let us know if you need more details.

---

### Post by cariboo on 2008-08-22
It would be even easier if you insert the livecd and installed ndiswrappper from the cd. If you are browsing the cd look in /pool/main/n

Jim

---

### Post by nike4ani1 on 2008-10-09
i have tried to check the synaptic package manager but could not find any thing like 'ndiswrapper' so plz help me in installing it
i m just a beginner in linux, i m using ubuntu 6.06 
i went to synaptic package manager afterreading few threads but could not find it there even,
i really want my wifi card to work with linux.
:(

---

