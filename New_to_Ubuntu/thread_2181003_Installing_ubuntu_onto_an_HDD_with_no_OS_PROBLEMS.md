---
title: "Installing ubuntu onto an HDD with no OS PROBLEMS"
date: 2013-10-15
forum: New to Ubuntu
---

### Post by JACXefY on 2013-10-15
I've been using a USB with a ubuntu iso file on it and am trying to install it onto a HDD but when I go to install it doesn't even give me the option of installing it to that HDD. I've looked in the BIOS and the computer does recognize the HDD as being there. I was wondering if connecting that HDD to another desktop and moving the iso file into it would work? If not do you guys have any solutions?

---

### Post by heir4c on 2013-10-15
Is there already some OS installed on that HDD or not? (What I understand in your question, there is not a OS on it)
Open the program gParted (Partition Manager) and look there if the HDD is recognized. (Maybe you take a screenshot and put it here (first upload it to a upload website and put here the link to it.)
Maybe there is no partition on it so you must first create a partition on it. (One thing you can see in gParted is that the HDD is Unallocated)

---

### Post by JACXefY on 2013-10-15
How long does gparted usually take? It has been running for close to ten minutes and hasn't done anything (still scanning all devices). When I try and install it i get to the 3rd step and it asks where to install it to(installation type), but I have no option the list where partitions are listed are empty and the bottom option bar (Devide for boot loader installation) says /dev/sda and I cannot change it.

---

### Post by Bucky Ball on 2013-10-15
You need to boot from the CD, NOT move the ISO to the hard drive. That will achieve nothing and is not the way to install. 

Get into the BIOS and set it to boot from the CD, not the first hard drive.

Incidentally, dropping the ISO to a CD will not work either. You need to make a bootable disk to install. 'Burn Image'. Use whatever Win CD burning software you use to do it. NOT make a data CD. Won't work.

---

### Post by JACXefY on 2013-10-15
I can boot from the USB flash drive I am using just fine the problem is that I cannot install it because ubuntu cannot find my HDD. TO my knowledge CDs and USB flash drives both work.

---

### Post by squakie on 2013-10-15
<<<EDIT: I should have started this with "while booted from cd or usb....."  >>>

Open a terminal window and try the following and post back:

sudo blkid <press enter>

sudo df -h <press enter>

ls -al /dev/disk/by-uuid <press enter>

---

### Post by JACXefY on 2013-10-16
Thank you everyone, sorry for wasting your time I changed HDDs and it worked fine, that one must have been faulty or something!

---

### Post by Bucky Ball on 2013-10-16
All good. Please mark as 'solved' from thread tools at top right to help others.

---

