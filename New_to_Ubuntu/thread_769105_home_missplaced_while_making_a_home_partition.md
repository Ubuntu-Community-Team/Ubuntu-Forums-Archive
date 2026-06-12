---
title: "/home missplaced while making a /home partition"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by Mark_in_Hollywood on 2008-04-26
My /home has been emptied by mistake.

I was making a separate partition for it and something went wrong. I have the data of /home backed up on another drive not connected to the computer at the moment. 

I'm in a LiveCD session.

[B]ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000080

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7687    61745796   83  Linux (60 gig)
/dev/sda2           38537       38913     3028252+   f  W95 Ext'd (LBA)
/dev/sda3            7688       38536   247794592+  83  Linux (230 gig)
/dev/sda5           38537       38913     3028221   82  Linux swap / Solaris

Partition table entries are not in disk order[/B]

I would have posted the /etc/fstab of the above disk, but, I don't know where to look for it. Neither of the two partitions /sda1 /sda3 show anything other than what APPEARS to be the LiveCD folders.

I was sudoing along, when I got some error messages. I made a text file and saved them to my Desktop, but on reboot I can't get to the desktop, because, both partitons of the /dev/sda show nothing in them. Also the first time on reboot, after the messup, the graphic splash error message was the "there was no /home/mark and I could log in as / or some such message. I was following commands from PsychoCats page on a separate /home partition and the command-line page PsychoCats links to at the top of his page.

---

### Post by 123456789123456789123456 on 2011-01-20
is the /home folder gone?

if so, use following command, from the live cd, get the name that the live cd has for your hard disk, for instance it would be in /etc/media I think, been a while.  and also locate the name of the other drive that has the /home in.  if necessary, create the folder home in that disk, copy files to the folder, use in terminal

sudo cp -r /../media/drive name/home/ /../media/original ubuntu drive/

note: cp -r, copy recursive, makes an exact copy, recreating folder name, and recreating sub folder names, it then copies all files to the respective folders. that may resolve the issue.

---

