---
title: "[SOLVED] Partition table help please!!"
date: 2008-09-07
forum: New to Ubuntu
---

### Post by madrussian on 2008-09-07
Hello all, I have just installed Ubuntu on my Second box and Keep getting an unrecognizable partition table for drive 80 non compatible FDISK tool (error 116).I have Windows Media edition and Ubuntu 8.04 and this only pops up when i go into ubuntu.Both Os work fine just curious about the message and trying to learn as i go.thank you

---

### Post by caljohnsmith on 2008-09-07
Can you first post the output of the following so we know what you are seeing? 
```
sudo fdisk -lu
```

---

### Post by madrussian on 2008-09-07
Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xcab10bee

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   372884714   186442326    7  HPFS/NTFS
/dev/sda2       372900780   390716864     8908042+   c  W95 FAT32 (LBA)
justin@justin-desktop:~$ 



Here is what i get, I dual booted my other box xp pro and hardy with no problem.The only obvious difference to me is my backup drive on this machine???

---

### Post by caljohnsmith on 2008-09-07
Do you have more than one HDD? Because your fdisk output only shows one HDD, sda, and it doesn't have any Linux partitions, only Windows (or NTFS to be exact). Where exactly are you seeing the "unrecognizable partition table for drive 80 non compatible FDISK tool (error 116)" error?

---

### Post by sandysandy on 2008-09-07
see here also

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

regards

---

### Post by madrussian on 2008-09-07
> **caljohnsmith said:**
> Do you have more than one HDD? Because your fdisk output only shows one HDD, sda, and it doesn't have any Linux partitions, only Windows (or NTFS to be exact). Where exactly are you seeing the "unrecognizable partition table for drive 80 non compatible FDISK tool (error 116)" error?

I have one hard drive,and a backup drive for windows restore.When i install hardy i used windows to install via the menu on the disk.I thought it would have set a separate partition for Linux but i am very unfamiliar with most things computer related at this point.

After I boot and the HP invent screen,I get a menu to Load 
 Windows Media Edition
 Recovery for windows media edition
 Ubuntu

When I choose Ubuntu that is the only time i get the Error message.after a brief second Ubuntu loads ( it doesn't go through all the checks and ok's my other computer does) the Ubuntu loads with no worries..

Is this error a major problem or is it something i messed up somehow and can easily be fixed???thanks

---

### Post by caljohnsmith on 2008-09-07
OK, that explains it: you actually did a Wubi Ubuntu install where Ubuntu gets installed into Windows without creating its own partition. If you want to try and get your Wubi installation working, I would recommend posting to the "wubi" ubuntu forum category, as I'm sure you will get more relevant help there. 

But if you don't mind letting Ubuntu have its own partition, that is definitely better than a Wubi install, because a Wubi install just adds one more layer of complexity where things can go wrong (and that may be why yours isn't working). So if you are OK giving Ubuntu its own partitions, first defragment your Windows partition from within Windows; next boot your Live CD and go through the install process, but choose "manual" for partitioning so you can then set up partitions for Ubuntu. For a normal install you will need two partitions for Ubuntu, one for the main file system which will be mounted on "/", and one partition for swap space.

If you need more details/help, let us know.

---

### Post by madrussian on 2008-09-07
OK thank you, both OS work fine but definitely want to have everything working properly and set correctly.

So what will happen after i defrag and reload hardy??? Will i have to delete my Ubuntu that is on my windows partition? (i would guess yes)but have never messed with moving or changing partitions.Any advise or guidance would be greatly appreciated,Thanks again!!

---

### Post by caljohnsmith on 2008-09-07
> **madrussian said:**
> OK thank you, both OS work fine but definitely want to have everything working properly and set correctly.

So what will happen after i defrag and reload hardy??? Will i have to delete my Ubuntu that is on my windows partition? (i would guess yes)but have never messed with moving or changing partitions.Any advise or guidance would be greatly appreciated,Thanks again!!
Yes, I don't think there is any easy way to migrate a Wubi install into its own partition; in fact, it may be next to impossible to do so without alot of effort and hassle (but I could be wrong). If you can back up any files you have in your Wubi install, I would do that and go ahead and delete it, and then install Ubuntu to its own partitions.

---

### Post by madrussian on 2008-09-08
> **caljohnsmith said:**
> Yes, I don't think there is any easy way to migrate a Wubi install into its own partition; in fact, it may be next to impossible to do so without alot of effort and hassle (but I could be wrong). If you can back up any files you have in your Wubi install, I would do that and go ahead and delete it, and then install Ubuntu to its own partitions.

THANK YOU again for your help with this,So i Basically made a virtual Ubuntu within windows?How can I delete all the files for the Wubi Install?Would you recommend partitioning my 200gig drive or just add a second drive and just put Hardy on that by itself?
( I have some spare drives lying around)thanks

---

### Post by caljohnsmith on 2008-09-08
> **madrussian said:**
> THANK YOU again for your help with this,So i Basically made a virtual Ubuntu within windows?How can I delete all the files for the Wubi Install?Would you recommend partitioning my 200gig drive or just add a second drive and just put Hardy on that by itself?
( I have some spare drives lying around)thanks
You're welcome, hope your soon-to-be installation goes OK. :)

I did a quick look at the Ubuntu help website, and it looks like it is actually possible to migrate a Wubi installation to its own partition:
[http://lubi.sourceforge.net/lvpm.html](http://lubi.sourceforge.net/lvpm.html)
But, I personally would not do that as you could easily run into all kinds of problems. So to uninstall Wubi, here's the official Ubuntu documentation:
[https://wiki.ubuntu.com/WubiGuide#head-7cd5a1eda23f1e9960c28ef3a2f4e8645c5ea87d](https://wiki.ubuntu.com/WubiGuide#head-7cd5a1eda23f1e9960c28ef3a2f4e8645c5ea87d)
It looks like all you have to do is run your "Add/Remove Programs" in Windows and simply uninstall the "Ubuntu" program. 

About using your 200 GB drive or adding another HDD for Ubuntu, either would work fine, so it is totally up to you. But I personally would go ahead and let Ubuntu have its own HDD as long as you have one, that way it is less risky compared to trying to repartition your 200 GB drive.

Let me know how it goes. :)

---

### Post by madrussian on 2008-09-09
I finally got everything set up and working properly, I installed manually and put on a seperate drive (13Gig) and everything seems to be working 
properly.

I have one final question on my install: Even though I used a separate HDD is it possible that it could role over so to speak into my larger HDD because on space limitations? I manually set it up to format and use the small one only.


Thanks Again 
Justin

---

### Post by caljohnsmith on 2008-09-09
> **madrussian said:**
> I finally got everything set up and working properly, I installed manually and put on a seperate drive (13Gig) and everything seems to be working 
properly.

I have one final question on my install: Even though I used a separate HDD is it possible that it could role over so to speak into my larger HDD because on space limitations? I manually set it up to format and use the small one only.

Thanks Again 
Justin
13 GB seems a bit cramped, and you could easily reach that limit depending on what programs you install and what other data (especially media) you put on that HDD. Certainly you could use your larger HDD for storing all your personal media, documents, etc, but all your Ubuntu programs would have to be installed on your 13 GB HDD, which you could fill up quick. It just depends on what you plan on doing, so I can't give you a definite answer. Glad everything is working OK though. :)

---

