---
title: "ubuntu Boot failed: not a bootable disk"
date: 2017-03-09
forum: New to Ubuntu
---

### Post by ryancostigan on 2017-03-09
Hi, 

I am getting the error Boot failed: not a bootable disk.

I have booted the server off of a boot-repair-disk iso.
It does not give me the option of recommenced repair or advanced options.
I did however get the paste file: [http://paste.ubuntu.com/24145062/](http://paste.ubuntu.com/24145062/)

I am quite new to Linux so if anyone could offer some advice.

Regards, 
Ryan

---

### Post by yancek on 2017-03-09
What are you trying to boot?  The boot repair output shows one 53.7GB drive which has no partition table and no partitions on it so there is nothing to boot.  Did you try to install some operating system on this drive?

---

### Post by ryancostigan on 2017-03-09
Hi, 

There was ubuntu server installed and has been running on it for a few weeks, the oldest backup for 2 week ago gives the same error when we restored it, but the original image of the server boots when we restore it.

Regards, 
Ryan

---

