---
title: "first timer trying to install Ubuntu for dual boot"
date: 2008-08-04
forum: New to Ubuntu
---

### Post by punkinold on 2008-08-04
I am an absolute beginner with anything outside of windows and standard trouble shooting.  I decided it would be interesting to look at and learn some Linux since I just bought a new machine for the family and upgraded my old machine, the one I wish to dual boot with. HP Pavillion 752n 60GB HD, 1GB ram.

I cannot get past the partiton screen.  Each time it gives me a "to small" error.  I have over 20GB of space available.  What should I be doing, I tried everything including manual partition.

I would love to learn more.  HELP!!

---

### Post by cdtech on 2008-08-04
Have a look at this thread:
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by Paqman on 2008-08-04
> **punkinold said:**
> 
I cannot get past the partiton screen.  Each time it gives me a "to small" error.  I have over 20GB of space available.  What should I be doing, I tried everything including manual partition.


When does this error pop up? When you try to resize the NTFS partition? How much free space does the NTFS partition have? Have you defragged it?

---

### Post by dhughes on 2008-08-04
And is it XP or Vista? I've read a recent update made Vista/Ubuntu dual booting a bit tricky.

---

### Post by punkinold on 2008-08-04
It's XP.  I rebooted again and it started to partition then errored.  In frustration I forgot to write down the message.  I am done for the night and will try again tomorrow.  Any suggestions will be welcomed, plus more information on the error tomorrow!

Thanks

---

### Post by dhughes on 2008-08-05
I'm not sure what the trouble is, 'too small'? Maybe you're trying to install to the swap partition :confused: but I don't know if that was tried if an install would even try to do such a thing. Maybe you made the Swap partition too small, but I don't know if you would see an error message if you did that.
 
 Maybe you could try partitioning using the LiveCD and the Gparted partitioning application before the actual Ubuntu install (avoiding the partitioning part of the install...maybe you got confused there) and then just select the partition when going through the install process again, probably sda2. Make a Linux Swap of 2GB and the rest, 18GB, is ext3, then try to install Ubuntu.

---

