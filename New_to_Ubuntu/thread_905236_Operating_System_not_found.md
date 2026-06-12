---
title: "Operating System not found"
date: 2008-08-30
forum: New to Ubuntu
---

### Post by saitham on 2008-08-30
Two days ago, I downloaded the last upgrade. After finishing the upgrade, the screen was frozen. couldn't even move the courser. Now I restarted my laptop, but all I get is a black screen telling me "Operating System not found". I already checked the BIOS, but everything seems to be OK. Does anyone here had the same problem and knows how to solve?

Thank you in advance!

---

### Post by overdrank on 2008-08-30
> **saitham said:**
> Two days ago, I downloaded the last upgrade. After finishing the upgrade, the screen was frozen. couldn't even move the courser. Now I restarted my laptop, but all I get is a black screen telling me "Operating System not found". I already checked the BIOS, but everything seems to be OK. Does anyone here had the same problem and knows how to solve?

Thank you in advance!

Hi and welcome, I have not seen this issue, but do you still receive the grub? You may try and reinstall the grub if not.

Move to ABT. :)

---

### Post by stevoo on 2008-08-30
i would reccon the grub went corrupted.

If you have the ubuntu cd you can reinstall the grub boot screen and see what happens

---

### Post by Gone fishing on 2008-08-30
I'd boot on the Ubuntu live disk check the Ubuntu partition exists and assuming it does fix grub.

This is how to fix grub

Open a terminal and type:

sudo grub

> root (hd0,0)

> setup (hd0)

> exit

This is assuming your Ubuntu partition is at hd0,0 the first hard drive and the first partition on that drive, If not, then adjust accordingly. (To find where your Ubuntu boot  partition is if you don't know,  after sudo grub type "find /boot/grub/stage1" and use that value. (If you not sure how grub names disks have a look at: [https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto))

This isn't quit how I do it I put grub on my Linux partition (hd0,0) (in this case) (> setup (hd0,0)) and then use the GAG boot loader gag.sourceforge.net

---

### Post by bumanie on 2008-08-30
It is possible that your partition table has been corrupted by some means. Messages such as 'no operating system found' or no disk is usually a 'whacked' partition table. The only way to try and retrieve it is by using the live cd of testdisk and having it re-write your partition table. You can get [testdisk here]("http://www.cgsecurity.org/wiki/TestDisk")Read the instructions to ensure you understand what you are doing before using it - it is quite easy to follow, but do a bit of reading first.

---

### Post by Gone fishing on 2008-08-30
> I already checked the BIOS

However, it also comes to mind that you might be trying to boot off the wrong device.

---

