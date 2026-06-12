---
title: "format!!!"
date: 2008-11-17
forum: New to Ubuntu
---

### Post by frost151n on 2008-11-17
hello, umm.. In windows in 'My Computer' you could right click on a removable drive to format it!!
How do you do that on Ubuntu???

---

### Post by tuxulin on 2008-11-17
do a "fdisk -l" to help find your drive then
do a little read up on the command "mkfs" as it
is the command not only to format the partition/hhd
but it allows you to create a new file system too

good luck
TUX

---

### Post by bobnutfield on 2008-11-17
An even easier way is to install Gparted:

> sudo apt-get install gparted

This is a GUI partitioner and makes partitioning and formatting a breeze.

---

### Post by Norfeldt on 2008-11-17
If you are not used to the terminal do the following things:
Applications/ Add/Remove..
Make it show: All available applications
Search for: gparted
Mark the "Gnome Partitions Editor"
Press "Apply Changes"
It will now install it.
After installation it will be in System/Administration/Partitions Editor
If it isn't there then try to log out and log ind again. Perhaps restart the computer.
The rest should be easy..

---

### Post by blesbok on 2008-11-17
i did the following on Fedora: (note for vfat filesystem which is window$ compatible)  The -I was necessary for success

```
mkfs.vfat /dev/sdc -I
```

for Ubuntu: (sda will need to be replaced with the relevant drive name)

```
mkfs.vfat -F 16 -n /dev/sda
```

good luck :)

---

### Post by frost151n on 2008-11-18
i think i'll try the gparted thing. Thnx everyone!

---

