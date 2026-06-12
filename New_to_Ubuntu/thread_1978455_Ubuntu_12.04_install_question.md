---
title: "Ubuntu 12.04 install question"
date: 2012-05-11
forum: New to Ubuntu
---

### Post by myolbug on 2012-05-11
Ok, I have in the past installed many varieties of Ubuntu and Mint, but I am trying a couple of things different today and I need assistance.

To start, I have a Gateway NV52 laptop with Win7 and Mint.  I am trying to delete the Mint partitions and resize (increase) the Windows partition.  

Using an Ubuntu 12.04 DVD I have so far deleted the EXT4 partition and resized the NTSF partition, but I am stuck now because when I hit install from the partition screen, I get an error message that states:
No root file system is defined.  Please correct this from the partitioning menu.

How do I do this, I do not see a menu as an option.

The DVD is still in, so I am able to quit and undo what I have done, I guess.  I need Win7 on this machine, and that is really my only concern is keeping that, as I have certain programs for my office on it.

Thanks!




Ok, more info,  Apparently when I deleted the partition that had Mint on it, I deleted the grub too, as I cannot log into my computer, even to Windows.  Right now it is saying GRUB loading.  Error: No such partition.  What do I do?

---

### Post by traditionalist on 2012-05-11
> **myolbug said:**
> Ok, I have in the past installed many varieties of Ubuntu and Mint, but I am trying a couple of things different today and I need assistance.

To start, I have a Gateway NV52 laptop with Win7 and Mint.  I am trying to delete the Mint partitions and resize (increase) the Windows partition.  

Using an Ubuntu 12.04 DVD I have so far deleted the EXT4 partition and resized the NTSF partition, but I am stuck now because when I hit install from the partition screen, I get an error message that states:
No root file system is defined.  Please correct this from the partitioning menu.

How do I do this, I do not see a menu as an option.

The DVD is still in, so I am able to quit and undo what I have done, I guess.  I need Win7 on this machine, and that is really my only concern is keeping that, as I have certain programs for my office on it.

Thanks!

You need to set a mount point as "/root", also be very careful what you check when asked where to install the loader, I overlooked this a couple of times and it caused problems.

I can't give you a screenshot of the install for obvious reasons.  But here is what it looks like in the disc utility;

---

### Post by ajgreeny on 2012-05-11
First thing to do is shrink the windows partition with windows own disk management tool; it is probably sfaer then using a linux utility.

Now at the disk preparation stage of the installation choose "Something else" which allows manual partition management.  Here you can now choose the free unallocated space and make a new ext4 partition which has the mountpoint / and with a tick in the format box.  The old swap will be used if you did not delete that as well as the Mint partition.

---

### Post by myolbug on 2012-05-11
Well, I figured it out and all is well in the world.  I reinserted the Ubuntu 12 Live DVD and selected it to install alongside.  This fixed it.  Very simple and I have everything back.  

Love the simple fixes!

---

### Post by traditionalist on 2012-05-11
> **myolbug said:**
> Well, I figured it out and all is well in the world.  I reinserted the Ubuntu 12 Live DVD and selected it to install alongside.  This fixed it.  Very simple and I have everything back.  

Love the simple fixes!

Sorry, I got booted out trying to post the screen shots.  Happy to hear you got it fixed anyway.

Regards....Trad

---

### Post by baldawat on 2013-01-21
I am also having same problem, not  able install ubuntu over Windows 7. During installation it is giving error
 
No root file system is defined. Please correct this from the partitioning menu.
 
My system configuration:
 
Processor: AMD Phenom(tm) II X4 B97 - 3.20Ghz
HDD: 350Gb
RAM: 4Gb
OS already installed: Windows 7 (64-bit)
Having four partitions:
1. C - OS Installed (99Gb)
2. D - Data Drive (66Gb)
3. F - Data Drive (66Gb)
4. System Reserved Partition (100Mb)
 
Want to install Ubuntu by modifying F Drive? 
 
But installer is not able to access partitioning menu.
 
Please help by your valuable feedbacks.

---

### Post by mastablasta on 2013-01-21
you porbably have too many primary parittions. can you open widnows disk manager in windows and check? you need to have max 3 primary parittions.

---

### Post by audiomick on 2013-01-21
Yes, I think mastablasta is probably right. Can you move all of the data from the F partition into the D partition and then delete F (using the windows tool)?

---

### Post by baldawat on 2013-01-21
I have tried that but still it is not working.

---

