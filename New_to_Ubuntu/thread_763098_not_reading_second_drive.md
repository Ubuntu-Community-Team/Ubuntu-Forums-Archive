---
title: "not reading second drive"
date: 2008-04-22
forum: New to Ubuntu
---

### Post by waggingwabbit on 2008-04-22
i have ubuntu installed already, but prior to this i had backed up some files from XP to a second hard drive. it has nothing but files i backed up from when i used XP. i tried plugging it back into the same secondary IDE or whatever plug it used to be plugged in. when i go sys>pref>hardware info, it shows up as /dev/hdd, but i can't mount it. also, it doesn't show up anywhere else. when i type in blkid or ls -l /dev/disk/by-uuid/ it doesn't show up... can anyone help me out with this? im trying to bring all my files from that drive to this one.

---

### Post by Moop on 2008-04-22
Try following the steps in this tutorial.
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by waggingwabbit on 2008-04-22
i dont think thats going to work for me. when i go to my fstab i can't even find my hard drive there. there is no windows partition in the drive in trying to install. it just has some data files in NTFS format. there are no windows folders/directories in it. when i press del while the computer is starting up i can see in the bios that the hard drive is read properly by it. how come ubuntu doesn't see it or ignores it?

---

### Post by Moop on 2008-04-22
It doesn't matter that windows isn't installed on that hdd. What does 
```
sudo fdisk -l
``` show you? Does it show up there?

---

### Post by waggingwabbit on 2008-04-22
no...it doesnt show up =[

---

### Post by Moop on 2008-04-22
Check the jumper on the hard drive and make sure it's set to CS or slave if it's not a sata hdd.  Have you tried mounting it from a live cd? Boot up a live cd and see if it mounts.

---

### Post by waggingwabbit on 2008-04-23
it shouldn't be set at anything else...its been the slave all this time and i haven't changed it. 

i tried the live cd and it doesn't mount there either. it shows up as "unalocated" in the gnome partitioner though... where it says used and free space its empty with no numbers...this doesn't look good to me.......

---

### Post by Moop on 2008-04-23
It sounds like the partition table is messed up. You could try recovering it with TestDisk or maybe hooking it up to a windows pc would let you get the data. 
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

