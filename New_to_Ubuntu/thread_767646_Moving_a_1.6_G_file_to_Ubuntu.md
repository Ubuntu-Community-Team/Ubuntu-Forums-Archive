---
title: "Moving a 1.6 G file to Ubuntu"
date: 2008-04-25
forum: New to Ubuntu
---

### Post by Porkchop_4 on 2008-04-25
I first looked at other threads and didn't see an answer to this problem.

I am trying to move a 1.6 G file (wmv) to my new Ubuntu platform and I am getting a message that "not enough space exists(?)"  I looked at disk space usage and I have 73 G free.  I tried moving to several different folders and I get the same message every time whether there is anything in the folder or not.  Any ideas?

---

### Post by superprash2003 on 2008-04-25
hey..are you trying to move a file from one drive to another or through LAN?

---

### Post by Porkchop_4 on 2008-04-25
I am moving from an external Iomega drive with Windows XP files to my LinuxCertified laptop.

---

### Post by superprash2003 on 2008-04-25
have you tried transferring those files to your Desktop .. i.e. /home/(user)/Desktop

---

### Post by Porkchop_4 on 2008-04-25
Yes, I am trying to drag and drop them - to a folder, Desktop or any other.

Here is a hint:  When I look at the property box on any Ubuntu folder it says I have 510.3 MB Free space.  This is quite obviously the problem.  How the heck do I reset this?

---

### Post by thisiam on 2008-04-25
when you installed ubuntu, did you install it to the whole drive or to a smaller partition?

---

### Post by superprash2003 on 2008-04-25
does that number increase or decrease when you add or remove a file? or does that stay constant?

---

### Post by Porkchop_4 on 2008-04-25
I didn't perform the installation LinuxCertified did.  This machine is all Ubuntu, no Windows!

I checked and that number (510 MB) seems to remain constant for Free space whether the folder has anything in it or not.  Strange, huh?

---

### Post by thisiam on 2008-04-25
what does this show you in terminal
sudo fdisk -l

---

### Post by Porkchop_4 on 2008-04-25
Here is what it said.  (What does all this mean?)

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1246    10008463+  83  Linux
/dev/sda2            1247        1381     1084387+  82  Linux swap / Solaris
/dev/sda3            1382        9729    67055310   83  Linux

---

### Post by Porkchop_4 on 2008-04-27
I think I figured this out after doing some reading.  I researched the *fdisk* command and something called an *fstab* file.

What I determined was the system was set up with three partitions on the hard drive a **10 G**, a **1 G** and a **67 G** partition.  The **1 G** is used for Memory functions, the **10 G** is what I see when I log on as root and by logging on as a user Greg (me), I can see the large partition...Or as root I can navigate to user Greg's home directory and I can see everything from root.

Anyway, I copied my home movies to the Greg home directory and everything copied fine.

But thanks, thisiam and superprash, for trying to solve my problem anyway.  I am understanding the Linux architecture a little better now.

Greg

---

