---
title: "need help please to prepare my sd card for using noobs installer"
date: 2019-09-11
forum: New to Ubuntu
---

### Post by romolnar on 2019-09-11
Hello, 


My name is roland, i'm from france. I need your help cause i'm trying to install raspbian using noobs (i downloaded it on raspberrypi.org website) but i am stuck on the "sd preparing level".


I use linux ubuntu 18.04, and i try to format my micro sd card using an sd adaptator and the internal sd reader of my laptop.


I used  gparted to delete and format my sd card to ext4 files system, and i succeeded, but that's when the pbms start. when i check the content of my sd card several things disturb me. I use the terminal to navigate in my sd card. First strange thing, the graphical file explorer says my sd card is empty, but when i go to the terminal and do a "cd /media/roland" then "ls", it displays 2 folders : one named "851138ce-5617-4671-94d3-2754b7bf6fec" and a second one named "NOOBS_v3_2_0" and this second one is empty. 


So i'd like to format a clean way the sd card in order to install then raspbian using noobs. I try to format it with gparted. It shows one partition /dev/mmcblk1p1 and tells me 336 MiB are used. I unmount, delete, "all operations successfully completed".Then i do "new partition", select ext4 file system option (i can't a partition name wich disturbs me). Ok "all  operations successfully completed". And it shows me again one partition with 336Mib used. I return to the terminal, cd /media/roland and ls and i stil have a "NOOBS_v3_2_0" folder. 


Anyone could explain me what's wrong with me??? PLEEAAASSSEE.... It's 3 days i try to get rid off this and i begin to feel tired...


Thanks in advance,


roland

---

### Post by TheFu on 2019-09-11
Most of the time, you need an empty SD card and a binary OS image for a raspberry pi.  Then you would use a tool like dd, **ddrescue** to do a bit-for-bit copy of the image file onto the SD storage.

There is no need to format the SD card, since the image is going to overwrite that and includes the needed format already.

---

### Post by him610 on 2019-09-11
Did you follow the installation guide located here, [https://www.raspberrypi.org/documentation/installation/installing-images/linux.md]("https://www.raspberrypi.org/documentation/installation/installing-images/linux.md")
This is the English version, but I would think there is a French version available.
I have completed the Raspbian installation on my Rpi2 and Rpi3 several times without issue; however, I **always** follow the referenced guide.

---

### Post by romolnar on 2019-09-11
Hello! Thank you so much! 
i followed another one with noobs but i will follow your link it is much more detailed and clear!!

---

