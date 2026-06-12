---
title: "Slow Restart"
date: 2008-11-14
forum: New to Ubuntu
---

### Post by vondy0 on 2008-11-14
I am very new to Linux so I am piecing things together. When I restart my computer it shuts down and then is completely blank and for five minutes. Then it says: acpid: exiting
Then it starts up. When I am at my boot menue there are two four Ubuntu options. 
Ubuntu 8.10, Kernel 2-6-27-8-generic
Ubuntu 8.10, Kernel 2-6-27-8-generic (recovery mode)
Ubuntu 8.10, Kernel 2-6-27-7-generic
Ubuntu 8.10, Kernel 2-6-27-7-generic (recovery mode)

My motherboard is a 64 bit ASUS P5Q SE/R if that is needed. Anyone's help would be very appreciated.

---

### Post by mapes12 on 2008-11-14
Can't say for certain but it looks like you have installed 8.10 twice? Hence the problem. Have a look at your partitions with a good GUI like GParted. It's on the live CD or from its own website. Also, have a look at the installation guides from Pyschocats in my sig file.

If you can take a screen shot of the GParted results then post here and we will see what we can do to help further. Alternativley, ```
sudo fdisk -l
``` in Terminal and post here will give us a start.

---

### Post by ajgreeny on 2008-11-14
No, I don't think you have installed twice, I think you have the two kernel versions, the original from installation and the updated version.  Note the numbers at the end of the twinned pairs are different, 7 and 8.

However, that doesn't help particularly, and I'm afraid I can't imagine what the problem may be, but it would be very useful to see your hardware.  Either just list what you have or if you don't know exactly your hardware, in a terminal type ```
sudo lshw > hardware.txt
``` and post the hardware.txt file that appears in your /home as an attachment here.

---

### Post by bswilson on 2008-11-14
Just a quick follow-up to **mapes12's** post.  You can get **gparted** from the Ubuntu Repositories:

```
sudo apt-get install gparted
```

---

### Post by mapes12 on 2008-11-14
```
sudo lshw
```
Will keep the output in Terminal instead of taking it to your /home folder. But, yes, missed the kernel version end numbers. Either way your partition set up is important and the output as previously posted will help.

> Just a quick follow-up to mapes12's post. You can get gparted from the Ubuntu Repositories:But run it off a CD at boot up otherwise it will not report a mounted partition i.e. the space where your OS is working off.

Also, have you got anything on this machine that would be an issue if you were to reinstall? The first to go is usually Firefox Bookmarks but if you install the Firefox plugin "Foxmarks" they can be backed up via your Foxmarks account. It's free.

---

### Post by vondrp on 2008-11-14
Here is the partition information and my hardware. Thanks a lot guys. You are all being very helpful!

---

### Post by vondrp on 2008-11-14
I can reinstall if I have to. I know that I did not originally have the duplicate kernel. Could it have happened during an update? The slow restart was there before the duplicate kernel.

---

### Post by mapes12 on 2008-11-14
OK. Windoze (sda1) dual boot with Ubuntu installed on sda5. Have you got any personal files or the like on your Ubuntu installation? If not then go for a fresh install.

Likewise, if you have any important stuff on your windoze partition it might be wise to start with Ubuntu on a different machine (see attachment and get back to me for further info). Regardless, serious backup time. Yes, I know that all the guides advocate dual boot and so on but it only has to go wrong once and you're up the creek without a paddle. Been there and got the tee shirt!

---

### Post by vondrp on 2008-11-14
I do but i can just take them off. Ill do that now then. Once again, thanks a lot for all of the help.

---

### Post by mapes12 on 2008-11-14
Forgot to mention that 8.10 is still a bit buggy. 8.04 LTS would be my choice (and is on my machines).

---

### Post by LowSky on 2008-11-14
> **mapes12 said:**
> Forgot to mention that 8.10 is still a bit buggy. 8.04 LTS would be my choice (and is on my machines).

Don't spread such rumors, 8.10 is not "still a bit buggy."

Truth is 8.10 uses newer version of the Linux Kernel and many programs that are not part of normal installation have not always been tested fully. So a few people may run into some small issues.

---

### Post by ajgreeny on 2008-11-14
Also I note you have a swap partition of 9GB, huge for most users, especially if you have enough ram.  If you are running with 1GB ram or more I suggest you reduce your swap to about 1GB max.  If you have special reasons for the huge swap that I don't know about, ignore this.

---

