---
title: "usb hdd not listed"
date: 2008-11-29
forum: New to Ubuntu
---

### Post by jumpingjaxs on 2008-11-29
im new with linux and just average with computers and i would really really appreciate someone to follow through and help me with this problem. 

im using ubuntu 8.04 livedisk right now on a desktop pc.

i bought an external drive to back up my data but when i plugged it in, it doesnt show up. (i was told to type sudo fdisk-l in the terminal in order to mount it, but only my main internal drive is listed there).

someone told me to partition it so ive been reading about partitioning but now im soo confused. 

i just want to copy my data to this external usb drive before i try installing ubuntu.

can someone please guide me?

---

### Post by vgots on 2008-11-29
Have you tried to plug your external drive in a different usb port? By the way, some of external usb hdds have 2 usb connectors. So I have such one and when I plugged it in for the first time it didn't work, I've tried to stick in both connectors and everything worked fine. I guess it doesn't matter at all but...

---

### Post by davidbilla on 2008-11-29
vgots has got a point. Mine has two connectors of which only one works, for some reason! What's the size of your external hdd and how old is your system? I have a system which is a few years old and it doesn't recognize any external hard drive above 80 GB.

Can't you use your external hdd in your other OS in your PC?

---

### Post by corkscrew on 2008-11-29
Hi I'm no expert but i've had similar problems with usb hdd and a usb penstick, my hdd is ntfs and the stick is fat32 both can be read. However somtimes they are recognised when i plug in and somtimes not and no reason i can find. I've done all the fstab stuff and fdisk stuff spent days at it but i've found a very simple solution that i found by accident.

plug your drive in, then open a a terminal and type > lsusb
i think this forces pc to rescan usb ports a few seconds later and drives are mounted

---

### Post by corkscrew on 2008-11-29
Hi I'm no expert but i've had similar problems with usb hdd and a usb penstick, my hdd is ntfs and the stick is fat32 both can be read. However somtimes they are recognised when i plug in and somtimes not and no reason i can find. I've done all the fstab stuff and fdisk stuff spent days at it but i've found a very simple solution that i found by accident.

plug your drive in, then open a a terminal and type```
lsusb
```
i think this forces pc to rescan usb ports a few seconds later and drives are mounted

---

### Post by roscal on 2008-11-30
> **corkscrew said:**
> Hi I'm no expert but i've had similar problems with usb hdd and a usb penstick, my hdd is ntfs and the stick is fat32 both can be read. However somtimes they are recognised when i plug in and somtimes not and no reason i can find. I've done all the fstab stuff and fdisk stuff spent days at it but i've found a very simple solution that i found by accident.

plug your drive in, then open a a terminal and type 
i think this forces pc to rescan usb ports a few seconds later and drives are mounted


This sure fixed my problems. Man, I owe you a drink!
:)

Thanks corkscrew

---

### Post by roscal on 2008-11-30
lsusb

:)

---

### Post by m42tyger on 2009-01-04
just to add my 2c story:

i have a 500g freecom external network hard drive (NOT the pro version). for the life of me i couldn't get the thing to recognize as a USB hard drive, though it worked fine in file serve mode over the network.

nothing from lsusb, nor dmseg | tail, nor fdisk -l.

after reading the instructions verrrry carefully over again, i noticed that the pictures depict plugging in the usb cable BEFORE turning the drive on, something i hadn't done in the week i'd owned it. i usually let devices fully boot before plugging them in!

so whoever has problems with external hdds, try that before banging your head against the thing. :D

---

