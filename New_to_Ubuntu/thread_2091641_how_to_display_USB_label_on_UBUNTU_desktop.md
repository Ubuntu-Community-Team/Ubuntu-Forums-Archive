---
title: "how to display USB label on UBUNTU desktop"
date: 2012-12-05
forum: New to Ubuntu
---

### Post by mark allyn on 2012-12-05
Hello everyone,
 
I have an 8 GB sandisk USB flash memory and I can't get UBUNTU to display its label(s) on desktop when I insert the drive into the USB port. The drive has two partitions on it, both of them ext3. I am able to cp files successfully to the drive. If I do a sudo fdisk -l both of the partitions show up, and they show up in gparted as well. 
 
I can make the partitions visible on the desktop if I mount them, but simply issuing a "mount" command without mounting them from the command line does not show them in the list of devices. Furthermore, the two partitions do not appear in /etc/fstab even when I have them mounted.
 
One other point. When the drive is in the port, the flashing cursor in terminal takes a very long time to appear--may have something to do with the /etc/fstab bit.
 
Can anyone propose a solution to solve this problem?
 
Cheers,
Mark Allyn

---

### Post by gordintoronto on 2012-12-05
What version of Ubuntu? If it's a recent version, each of the partitions should appear in the Dash.

---

### Post by StinkySQL on 2012-12-05
I'm running 12.04 LTS and my 4GB thumb pops right up with the proper name, and also shows in devices named.

---

### Post by mark allyn on 2012-12-06
Hello gordintoronto and StinkySQL,
 
I'm running 12.04.1.  In essence, it doesn't do what StinkySQL says his does.
 
Cheers,
Mark

---

### Post by mark allyn on 2012-12-11
Hello everyone,
 
I found the problem.  Turns out I had used gparted and mislabeled the labels for the partitions on the flash drive.  Properly labeling them led to a nicely visible flash drive icon on the side panel and they mounted correctly at /media/sdb1, etc.
 
Cheers,
Mark

---

