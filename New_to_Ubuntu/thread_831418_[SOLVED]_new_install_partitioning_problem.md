---
title: "[SOLVED] new install partitioning problem"
date: 2008-06-16
forum: New to Ubuntu
---

### Post by chaddiesel on 2008-06-16
I have given up on upgrading to 8.04 and have resorted to using a live CD to reformat my linux partition.

Whenever I get to the partitioner on the live CD installer it won't let me do anything. What can I do? The partitioner will not bring up anything on the hard-drive that I can alter. The box is just blank.

:(

---

### Post by phidia on 2008-06-16
what does > sudo fdisk -l output? (type or copy/paste that into a terminal)
If your hard drive partitions are capable of being found you can use cfdisk for partitioning. It's a fairly easy partitioner to use. Type > man cfdisk in the terminal to learn more about that tool.

---

### Post by chaddiesel on 2008-06-16
It only says "Unable to open -"

---

### Post by chaddiesel on 2008-06-16
I got it to work a second time around....

> ubuntu@ubuntu:~$ sudo fdisk -1
fdisk: invalid option -- 1

Usage: fdisk [-b SSZ] [-u] DISK     Change partition table
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
       fdisk -s PARTITION           Give partition size(s) in blocks
       fdisk -v                     Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors

---

### Post by avtolle on 2008-06-16
l is lower-case letter "L", not the number 1.

---

### Post by chaddiesel on 2008-06-16
I copied and pasted the command and it doesn't do anything. Just brings up the next line for typing. No response at all.

---

### Post by avtolle on 2008-06-16
After ```
sudo fdisk -l
``` you should be prompted to enter your password. Is this what occurred? If so, did you enter your password (same one used to log on to the system) and then hit Enter?

---

### Post by chaddiesel on 2008-06-16
It didn't ask for the password. I'm not able to boot any linux kernel that I already have on the computer. I am on the live CD. I think that is my problem. 

Is there any way I can get this CD to install over my previous linux partition? 

I've never had a problem with a live CD before. :/

---

### Post by chaddiesel on 2008-06-16
What else can I do? 

1)I'm not able to get my previous kernels to boot at all.
2)I can't install over my linux partition.

Is there a way to delete ubuntu so I can try the install again?

---

### Post by phidia on 2008-06-16
It sounds like there could be a hardware problem.
If fdisk -l doesn't produce any results .. did you try cfdisk? Try that and copy and past the output from that.
You might also try [system rescue cd]("http://www.sysresccd.org/Main_Page").

---

### Post by chaddiesel on 2008-06-17
cfdisk provides a black screen and says:

FATAL ERROR: Cannot open disk drive
Press any key to exit cfdisk

I'm going to download and try the system restore cd.

---

