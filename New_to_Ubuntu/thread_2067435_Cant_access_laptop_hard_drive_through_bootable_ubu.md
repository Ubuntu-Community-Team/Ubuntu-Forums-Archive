---
title: "Cant access laptop hard drive through bootable ubuntu USB"
date: 2012-10-06
forum: New to Ubuntu
---

### Post by havefuninthesun on 2012-10-06
So windows 7 hard drive suddenly  decides to stop work, even though it was working perfectly the night before.

I was wondering if I could access my files using ubuntu on my flash dirve, or run chkdsk on my hard drive. I love the interface, just wish there was more software available for it.

Im brand new to this so sorry if this is answered somewhere else. I did search around for about half an hour but couldnt find anything.

---

### Post by greatsirkain on 2012-10-06
Same thing happened to me, I could access all my files in windows XP pro from Ubuntu, when it was fixed(ish) I ended up sticking with Ubuntu with a winXP installed as a safety net...It's just sat there eating up disk space now :P

---

### Post by havefuninthesun on 2012-10-06
> **greatsirkain said:**
> Same thing happened to me, I could access all my files in windows XP pro from Ubuntu, when it was fixed(ish) I ended up sticking with Ubuntu with a winXP installed as a safety net...It's just sat there eating up disk space now :P
How did you access your files on your windows XP?

was ubuntu installed on a flash drive or side by side with XP?

---

### Post by DuckHook on 2012-10-07
Please provide more info. Is your windows disk toast? If so, then nothing can be installed, including Ubuntu. Since you can still post to this forum, I assume that you have access to the Internet. Therefore, you can try downloading and burning a system rescue disk to determine and try fixing what is wrong. There are many such rescue disks available, but try to choose distros associated with reputable online sources like:

[http://sourceforge.net/projects/systemrescuecd/](http://sourceforge.net/projects/systemrescuecd/)

You can Google for others.

---

### Post by havefuninthesun on 2012-10-07
> **DuckHook said:**
> Please provide more info. Is your windows disk toast? If so, then nothing can be installed, including Ubuntu. Since you can still post to this forum, I assume that you have access to the Internet. Therefore, you can try downloading and burning a system rescue disk to determine and try fixing what is wrong. There are many such rescue disks available, but try to choose distros associated with reputable online sources like:

[http://sourceforge.net/projects/systemrescuecd/](http://sourceforge.net/projects/systemrescuecd/)

You can Google for others.

The SMART status is that the disk has a few bad sectors (209 to be exact). I booted ubuntu through a USB drive which is what Im using now, and yes, I have internet.

So I burn the disk image of a recovery program to a CD, and boot from that CD on startup?

And is there functionality  in ubuntu for simply accessing/copying files from a hard disk while booted from a USB?

---

### Post by greatsirkain on 2012-10-07
I booted from a live usb stick with ubuntu on it then mounted two hard drives including the dead one and swapped the files I wanted to keep over to the healthy one, it did it without much fuss. Bit of an eye opener with regards to winxp security

---

### Post by mips on 2012-10-07
> **havefuninthesun said:**
> 
And is there functionality  in ubuntu for simply accessing/copying files from a hard disk while booted from a USB?

Yes. If the drive is in not to bad a state you should be able to see the drive/partitions in the filemanager. If you can't then open diskutility and post a screenshot of the drive information.

The bad sectors could be located in a critical part of the drive where it defines the partition parameters etc and if that is the case then you won't be able to mount the partition. Your drive might be dying. If the bad sectors keep on increasing then it's a sure sign that the drive is on it's way out. You might as well post a screenshot with the smart info here as well.

---

### Post by Mark Phelps on 2012-10-07
Unfortunately ... you're up against two possible problems ...

First, if the partition filesystem is corrupted, you are most likely NOT going to be able to mount it in Ubuntu.  It has no way of overcoming filesystem corruption and if it detects that, it will simply refuse to mount it.

Second, there is no Linux equivalent of MS Windows CHKDSK.  So, if you can't mount the filesystem, your only recourse is likely to be removing the drive, connecting it to an MS Windows PC, and attempting to run CHKDSK from there.

---

### Post by havefuninthesun on 2012-10-11
Thanks for all the advice/links.

Unfortunately, I've realized that two out of five partitions simply wont mount. My main partition has an "Unknown()" file type, and it trying to mount in terminal does nothing.

This was a very good learning experience, though I did lose some stuff that I wish I hadn't lost. Thanks again.

---

### Post by mips on 2012-10-11
> **havefuninthesun said:**
> 
This was a very good learning experience, though I did lose some stuff that I wish I hadn't lost. Thanks again.

You could probably still recover it with some data recovery teqniques.

---

