---
title: "im running ubuntu 11.10 partitions and isomounts (no disc)"
date: 2012-02-27
forum: New to Ubuntu
---

### Post by phoenix940 on 2012-02-27
im new to linux and i just got ubuntu 11.10. i love it but unfortunately cant play many of my games on it hence the need for a second partition with windows 7 on it. i do not have the money or  access to dvds, cds, or a flash drive so i cant burn or otherwise transfer it to a hard disc and install it that way. i have gmount-iso to mount the file and gparted to manage the partition once its there. ive looked all over and i cant find a way to do wut i want that works on ubuntu 11.10... or more likely ubuntu 11.10 operated by me. but i would appreciate the help... im not very good at this yet but i do no how to use the terminal at least do very basic things like install. the simples wording would be most helpful however i realize there is no way to explain things without some tech talk because i am having a problem with a piece of technology.

---

### Post by lechien73 on 2012-02-27
Hi and welcome to the forums,

Could you just please clarify what you're trying to do? Are you trying to install Ubuntu, Windows 7, or the game?

---

### Post by phoenix940 on 2012-02-27
sorry i already have ubuntu installed... i would like to install windows 7 but i would like to keep ubuntu because i like it better all around. i would like to partition my laptop (toshiba satilite- 4gb ram/500gb hard drive) into two partitions and put windows 7 on it using gmount iso. i no this is probly pretty simple so thank u for taking the time to help a noob

---

### Post by phoenix940 on 2012-02-27
if there is a better way to do this than gmount iso then i would not be apposed to doing it without gmount iso i would just like 2 partitions one ubuntu and one windows

---

### Post by lechien73 on 2012-02-27
So, you have Windows 7 in an ISO file, correct?

You can re-partition your hard disk drive, to create room for Windows 7, using GParted on the Ubuntu Live CD.

As regards actually starting the install of Windows 7 from an ISO file, I don't know. As far as I know you'd need to create a CD or bootable USB stick in order to install it.

---

### Post by phoenix940 on 2012-02-27
yes and ok i tried that and in order to split my hard drive into partitions it says i have to manually unmount the partition? how do i do that? i cant find  it anywhere online... although i might just be horrible at google....

---

### Post by lechien73 on 2012-02-28
Hi - sorry for the delayed response. I'm really not doing a very good job of being away :)

You will need to boot in from an *Ubuntu Live CD/USB* and run GParted from there, after making sure the partitions on your hard drive are unmounted.

You can't make changes to a mounted partition, which is why you can't do it through the standard desktop.

---

