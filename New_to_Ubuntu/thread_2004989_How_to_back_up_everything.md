---
title: "How to back up everything?"
date: 2012-06-16
forum: New to Ubuntu
---

### Post by wilson888888888 on 2012-06-16
I have an old hard drive that i want to use as a backup drive. I used the instructions on this thread [http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087) to create a .tgz with all the stuff i need to back up, but i cant copy it into the old hard drive.

---

### Post by N0oki3 on 2012-06-16
Hi. 

The old drive you have, was plugged into PC before or you have just did it ? If you have just done it, it is becouse the disk is not formated properly for Linux. So download gparted and format it. Than it should work

---

### Post by wilson888888888 on 2012-06-16
I used gparted to put ext3 on it. I guess that its the right one, im not sure.

---

### Post by wilee-nilee on 2012-06-16
As a contrast I use clonezilla, a bootable cloner, it will save on a ntfs or ext partition.

Make sure the HD is not read only right now.

[http://clonezilla.org/](http://clonezilla.org/)

The method you have used is probably okay, I just notice that the reference thread is 7 years old is all.

---

### Post by wilson888888888 on 2012-06-16
It says i can only access files, but I can't change anything because i'm not the owner? How do i be owner?

---

### Post by wilee-nilee on 2012-06-16
> **wilson888888888 said:**
> It says i can only access files, but I can't change anything because i'm not the owner? How do i be owner?

You described formatting it to a ext3, this partition should be basically empty unless you have added anything.

Post a screenshot of gparted looking at it so we can see what is there.

Post it using the paperclip in the reply panel.

---

### Post by wilson888888888 on 2012-06-16
the screenshot

---

### Post by wilee-nilee on 2012-06-16
If you go to /media in file from the installed Ubuntu home left panel, and right click properties-permission on the HD does yours look like this.

[ATTACH]219819[/ATTACH]

---

### Post by wilson888888888 on 2012-06-16
no, it looks like this

---

### Post by wilee-nilee on 2012-06-16
Looks like the HD is in root, I could be wrong here.

What is in the partition now?

I'm just not familiar with using a tar.gz to back up,

With the one I mention, it saves as a image.gz, no restriction on the place saved except for the size of the image, I would use clonezilla.

You can look access the sdb in root I think.
```
gksudo nautilus
```From the install should allow access.

Clonszilla is for cloning it checks the image and saves the mbr as well, a lot easier method if you can follow the text imaging from the live cd.

You leave out the OS that you are running as well is it one that runs in root like backtrack, or are you running in root?

The tar.gz seems to save in root from what I can tell, could be wrong though.

---

### Post by wilson888888888 on 2012-06-16
Thanks, i used nautilus to copy the.tgz to the old hard drive.

---

