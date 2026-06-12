---
title: "How to dual boot Linux 13.04 and Windows 8?"
date: 2013-07-18
forum: New to Ubuntu
---

### Post by sharmaram on 2013-07-18
Hi,
My laptop shipped with windows 7 pre installed. Then i reformatted the HDD and installed windows 8. Now i want to run linux along with windows 8. My HDD structure is as follows.
C Drive: 50 gb
D Drive: 90 gb
E Drive: 90 gb
there are no any hidden partition except system reserved by windows.
i want to install linux by shrinking c drive. is this possible? if yes, how? i dont want to loose anything. If there is a guide to follow please please help. i really want to try linux and if satisfied would like to shift towards it.  i have already downloaded the required iso of ubuntu. i am absolutely new on this matter.

Thanks,
Ram

---

### Post by fantab on 2013-07-18
Yes, it is possible. Read this [How to]("http://www.liberiangeek.net/2012/11/shrink-resize-partitions-in-windows-8/").

Ubuntu needs atleast 2 partitions for itself:
25-30GB Ext4 '/' (for Ubuntu system files)
2-4GB SWAP

Windows partition with System Files needs atleast 25% of free space to run smoothly. 
If your current 'C' partition is where you have your system files then Shrinking that any further is not a good idea. Think of shrinking some other partition.

If you are using 'msdos' partition table on your HDD, which I think you are, then you have only 4 Primary Partitions Limit. There will be problems installing Ubuntu if you force a fifth.
To overcome this limitation you will have to create an Extended Partition, which is Primary Partitions and serves as a container for Logical Partitions.
Ubuntu can boot from a Logical Partition.

---

