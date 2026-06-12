---
title: "Extremely slow"
date: 2011-11-15
forum: New to Ubuntu
---

### Post by andis59 on 2011-11-15
Hello,
I have just installed Ubuntu on my Windows XP computer and it's really slow!
First I installed Ubuntu Desktop but it was so slow it was impossible to use. So I installed Xubuntu over it. It's still slow but it's a bit faster...
I have used sudo lshw to get the hardware, but I don't understand much of it. I attach it here:

It maybe that I have a slow computer, but XP runs normally, or to little memory or disk...

Please advise!


Thanks in advance!
// Anders

---

### Post by mike555 on 2011-11-15
If you want a faster computer do a fresh install of Lubuntu (not over anything), installing a desktop version over another one is not the best way.

---

### Post by snowpine on 2011-11-15
Probably you just need to install the correct driver for your ATI video card. I am not an expert on ATI cards so I recommend you do a forum Search for your **specific** card and/or use the Wiki: 

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

You'd have to compare Xubuntu to Windows 7 to be fair. Windows XP is over 10 years old and runs very quickly on older hardware (assuming no viruses/bloatware).

---

### Post by Toz on 2011-11-15
Unfortunately, the RV280 (9200) is no longer supported by ATi via the proprietary driver, so you're pretty much stuck with the radeon driver that you're using - which isn't necessarily a bad thing as long as you don't have any intensive 3D graphics/gaming requirements.

How did you install ubuntu? If I'm reading this correctly, your lspci file is showing that you have 2 drives (internal and external scsi) both with ntfs partitions? Is this a wubi install?

Your system should be powerful enough (P4 2.8, 512MB ram) to run xubuntu if you install it on one of your drives (dual-boot if you want to test). As mentioned previously, a straight xubuntu install will give you the best response. As well, Lubuntu is also an alternative lighter ubuntu O/S. You might also look around at getting another 256MB ram (if you can find some or have it lying around somewhere) to top up your system.

---

### Post by andis59 on 2011-11-15
Yes, I installed using wubi.
First time I installed Ubuntu desktop, but that was so slow that I couldn't do anything.
Then I resinstalled, using wubi, and selectec Xubuntu instead, but it's still very slow.

One thing I have wondered about is disk space. Since I have most of the disk for the XP system, only about 12 GB is available for Ubuntu. Can this have anything to do with it being slow?

I have used the task manager and cpu is never more than 40 % and memory is about 30 - 40 %

The program that is slowest if Firefox. If I have two tabs and switch between them it takes at least 30 - 60 seconds for it to change tab...

// Anders

---

### Post by Toz on 2011-11-16
Unfortunately, I am unfamiliar with wubi to comment on performance. However 12GB should be sufficient for an xubuntu or lubuntu dual-boot install. That should get you the best performance.

---

### Post by mikechant on 2011-11-16
I've never used wubi but lots of people claim it is *very* much slower than a proper native install for disc access.

Your CPU is fine; you could do with more memory - I know you are only seeing 30-40% use but maybe wubi is limited as to what fraction of the total memory it can use.

If you don't want to upgrade your memory, I'd recommend trying a native (non-wubi) install of Xubuntu, 12Gb is plenty for most purposes (as long as you're not going to store a load of data in the linux partition as well as the OS).

---

### Post by JKyleOKC on 2011-11-16
I installed via wubi on my laptop because I had too many proprietary apps on it to have room for a normal install, but use xubuntu as the only system on my desktop machines. The wubi installation runs at only about half the speed of the desktop machines. I only use it when I must; the laptop stays turned off most of the time anyway.

A normal install in 12 GB would not allow much room for large files such as pictures or movies, but would be plenty for running email, web browsing, and doing word processing. The amount of RAM is much more important than the amount of disk when it comes to determining system speed.

---

### Post by BBQdave on 2011-11-16
> **mikechant said:**
> I've never used wubi but lots of people claim it is *very* much slower than a proper native install for disc access.

Your CPU is fine; you could do with more memory - I know you are only seeing 30-40% use but maybe wubi is limited as to what fraction of the total memory it can use.

If you don't want to upgrade your memory, I'd recommend trying a native (non-wubi) install of Xubuntu, 12Gb is plenty for most purposes (as long as you're not going to store a load of data in the linux partition as well as the OS).

+1

And if you can give up the coinage for a stick of memory, it will go a long way in performance for your system.

I am running **Debian 6** and have run **Xubuntu** on my old notebook (dell inspiron 1100 with 2.0 celeron processor and 1 gig of ram), very responsive.  Though I do not dual boot, only one os, GNU/Linux :D

---

### Post by andis59 on 2011-12-20
I have been away for a while, but now I'm back...

I tried to install XUbuntu without using wubi, but it still was like molasses. So I bought 3GB of memory and now the computer is usable again.

Thanks for the help!

// Anders

---

