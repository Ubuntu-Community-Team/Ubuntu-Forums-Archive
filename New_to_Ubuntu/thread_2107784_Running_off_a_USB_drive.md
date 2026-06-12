---
title: "Running off a USB drive"
date: 2013-01-22
forum: New to Ubuntu
---

### Post by kb7kuh on 2013-01-22
Hi folks,

sorry for asking this but  how do I load Ubuntu onto a USB  Free Agent drive.  I can't remember what I have to do to the drive before loading.  It's telling me I don't have it setup correctly to install.   I'm currently running off the CD.

It says "No root file system is defined."

I remember I had to create the root, and a data section but I don't remember how to do it.

I did have it setup as a Duel Boot with Wondows7.

Thanks!

---

### Post by TOMBSTONEV2 on 2013-01-22
You have the partition set to ext4? Do you have a / for the mount point?

---

### Post by kb7kuh on 2013-01-22
Sorry I don't remember how to do that.  I'm running it off my laptop/CD Rom with the USB drive plugged in.  It sees the drive, but I cant remember how to setup the partitioning.

---

### Post by TOMBSTONEV2 on 2013-01-22
At the installation type select something else. At this screen you will select your usb drive(Make sure it is indeed the drive) then click "add" you will then proceed to allocate space for an ext4 partition and a swap partition. For the ext4 partition, make sure the mount point is set to "/" Then install to your ext4 partition. Note you can use ext3 as well.

---

### Post by kb7kuh on 2013-01-22
Thanks.  I will give it a try, and let ya know.

---

### Post by kb7kuh on 2013-01-22
OK,  I do not see a add selection.  I can select the correct USB drive.

---

### Post by TOMBSTONEV2 on 2013-01-22
The add button is right next to "New Partition Table" After clicking "add" a create partition box will pop up.

Let me see if I can find a guide or something for you with pictures;

[http://www.techspot.com/community/topics/step-by-step-beginners-guide-to-installing-ubuntu-11-10.172128/](http://www.techspot.com/community/topics/step-by-step-beginners-guide-to-installing-ubuntu-11-10.172128/)

Step 7 to step 8. The add button is visble in step 7-C. Their guide should get you sorted.

---

### Post by kb7kuh on 2013-01-22
I think I got it!  Thanks for your help.:D

---

