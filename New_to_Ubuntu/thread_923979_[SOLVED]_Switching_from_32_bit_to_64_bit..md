---
title: "[SOLVED] Switching from 32 bit to 64 bit."
date: 2008-09-19
forum: New to Ubuntu
---

### Post by jellmoo on 2008-09-19
Hi all,

I recently installed Ubuntu onto my Vista machine, and have been dual booting.

However, I installed the 32 bit version of Ubuntu, which does not seem to take advantage of my 6 gigs of RAM.  Because of this, I would like to switch to the 64 bit version.

Therefore I am wondering the following:

1) Is it possible to switch from the 32 bit to the 64 bit without uninstalling? 

2) If I have to uninstall and then install the 64b bit version, what would be the best way of going about doing so?

Thank you kindly!

---

### Post by haydnc on 2008-09-19
I've been thinking of doing something like this myself. (The whole 32 bit to 64 bit transition)

I would assume that it would be pretty easy just to install Ubuntu 64 bit right over the top of the 32 bit version... but I'm not quite brave enough to try it in case I'm wrong. ;)

Also, just in case anyone has an answer, last time I tried the 64bit version of Ubuntu it was handicapped by the vast lack of 64bit apps (coupled with the inability to run 32bit apps easily on the 64bit version). Does anyone know if this has been resolved yet? Does everything (pretty much) come in 32 and 64bit varities?

---

### Post by crazypenguin2008 on 2008-09-19
im pretty sure you have to dowload and burn the 64bit cd and do a fresh install. i could be wrong but i dont think i am

---

### Post by jellmoo on 2008-09-19
I've burned the 64bit CD, I'm mostly wondering if I have to remove the 32bit version first, or if I can can just pop the CD in and start a fresh install.

I'm a little worried that I'll end up with some sort of bastardized 48bit version of Ubuntu. :D

---

### Post by crazypenguin2008 on 2008-09-19
just do a fresh install. i allways just install over the previous version on my pcs

---

### Post by Sef on 2008-09-19
> just do a fresh install. 



That is correct.  Just reformat and install to the Ubuntu root partion.  The swap partition will be taken care of automatically if you have one.

---

### Post by pansz on 2008-09-19
Do you have anything to backup, or to preserved, in your current installation?

If not, just install the 64bit version, and choose to format the old partition when manually set the partition method. (yes you format it, and your 32bit ubuntu gone)


If you want to preserve something and you don't want to format your old installation: then boot with your 64bit livecd, mount your old partition at /mnt and manually rm -rf all of things you don't want. In most cases you want to leave /mnt/home there and remove everything else. After you umount your /mnt you can continue your installation.

---

### Post by crazypenguin2008 on 2008-09-19
i dont recomend the rm -rf commands to anybody personaly. its a good way to hose the OS if the wrong thing is removed and renders the os useless

---

### Post by Paqman on 2008-09-19
Yep, just reinstall straight over the top of your 32-bit version. Here's a handy tip for [reinstalling all your packages](http://ubuntuforums.org/showthread.php?t=261366).

In my experience, 64-bit is great. There used to be issues with Flash and Java that required the use of a 32-bit browser, but that's all been resolved.

---

### Post by crazypenguin2008 on 2008-09-19
+1  im running 64bit hardy on one of my amd quad cores and it run flawlessly

---

### Post by prshah on 2008-09-19
> **haydnc said:**
>  (The whole 32 bit to 64 bit transition)


> **jellmoo said:**
> I've burned the 64bit CD, I'm mostly wondering if I have to remove the 32bit version first, or if I can can just pop the CD in and start a fresh install.


You cannot install 64-bit "over" 32 bit; it will have to be removed first, or a side-by-side installation (different partition, you can share swap).

Taking into account that memory is the only problem you are facing, and your other concerns, I think you will be better off including PAE (Physical Address Extensions) support in the kernel. This will allow you to address upto 64 Gb (!!) of RAM, but it does require a kernel recompilation.

---

### Post by Tatty on 2008-09-19
Just boot a 64bit livecd, start the install, then at the partitoner select "manual partitioning".  Then just select your current ubuntu partition to be formatted and used as "/";

It will format your 32bit install and install 64bit.  Unless you have a separate /home partition then your /home folder will be formatted also, so back up!  (you should back up everything anyway before any sort of major system change like a new OS)

Just to be clear, there is no way of upgrading from 32bit Ubuntu to 64bit, it will have to be a fresh install.

---

### Post by jellmoo on 2008-09-19
Thanks everyone!  I will try installing 64bit this weekend.  I don't really have all that much to backup, so it shouldn't be too diffuclt.  The one issue I have is that I will have to re-configure World of Warcraft once again. ;)

Thanks again!

---

