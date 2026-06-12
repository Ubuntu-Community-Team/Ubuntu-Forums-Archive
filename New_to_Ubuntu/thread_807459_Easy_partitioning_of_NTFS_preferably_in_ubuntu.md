---
title: "Easy partitioning of NTFS preferably in ubuntu"
date: 2008-05-25
forum: New to Ubuntu
---

### Post by Qwaz_Dan on 2008-05-25
ive tried running partition magic from windows to splice my NTFS partition into an NTFS and a FAT32 partition, but i always get errors

what is the easiest way for me to create a FAT32 partition from the windows NTFS partition...

ive tried running a boot CD with Gparted on it aswell... and it doesnt seem to work.

---

### Post by tamoneya on 2008-05-25
running gparted on a boot CD is the general recommendation.  Could you tell us what exactly you tried and tell us where it failed.  That way we could probably get gparted working.

---

### Post by Qwaz_Dan on 2008-05-25
ok, im going to run it again so i can tell you exactly what happens

---

### Post by Qwaz_Dan on 2008-05-25
right heres what happens

i run gparted

choose default settings

lots of text flashes by as it loads

choose not to touch keymap

choose 0 for beginner mode

chose a low screen resolution

chose 02 British English (yes i like tea)

some more text flashes by and then it says

fatal server error
no screens found
XIO:fatal IO error 104 con reset by peer on X server ":0.0" after 0 requests (0 known processed) with 0 events remain.

casper@debian:~$

then i dont know what to put... ive told the computer jokes, sweet talked it, all sorts

what do you guys reckon?

---

### Post by maddot on 2008-05-25
if you have partition magic, what i normally do is resize your ntfs partition, so there is an empty space. then with that empty space create the fat32 partition. also, if you want to let the installation follow through, you could in theory let it create the ext and swap partitions as well and resize erm to fit.

IF that still don't work, try the alternate cd >.<

---

### Post by Qwaz_Dan on 2008-05-25
already tried resizing the NTFS partition to leave space... did not work

---

### Post by Paqman on 2008-05-25
> **Qwaz_Dan said:**
> 
then i dont know what to put... ive told the computer jokes, sweet talked it, all sorts

what do you guys reckon?

Sounds like you've used the Gparted LiveCD. Gparted is also on the normal Ubuntu LiveCD, which i'm you've got too. Stick it in and try again.

---

### Post by Qwaz_Dan on 2008-05-25
i cant see how to use the ubuntu CD to partition the drive without reinstalling ubuntu, how do i do this?

---

### Post by Qwaz_Dan on 2008-05-25
ok, worked that one out.. but gparted just seems to hang and say its scanning devices!!!

---

### Post by tamoneya on 2008-05-25
just give it a sec (a couple minutes)  It has to scan all your filesystems.  I dont see why it cant be faster but it isnt.

---

### Post by Qwaz_Dan on 2008-05-25
awesome, didnt manage to split the ntfs partition, but did make it into a fat32 one... which i can reinstall windows on without losing everything right :D

thanks for all the help guys

---

### Post by tamoneya on 2008-05-25
windows really prefers being installed on a NTFS.  Windows will definately give you some trouble if you try FAT32 if it is even possible.  I would try to get it onto NTFS if you can.

---

### Post by Paqman on 2008-05-25
The NTFS support in Linux is really good now, and it's a much better file system than FAT32.

---

