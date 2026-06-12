---
title: "[SOLVED] BAcking up an exact copy of whay I have now..."
date: 2008-08-11
forum: New to Ubuntu
---

### Post by NJ0E on 2008-08-11
Now that I have the system running like I want it, is there a way to save every thing in a backup file or an .iso image so that if I need to install it again I don't have to update 100 files agian?

Thanks  Joe

---

### Post by loboc on 2008-08-11
> **NJ0E said:**
> Now that I have the system running like I want it, is there a way to save every thing in a backup file or an .iso image so that if I need to install it again I don't have to update 100 files agian?

Thanks  Joe

look into dd

---

### Post by bpowell2005 on 2008-08-11
> **NJ0E said:**
> Now that I have the system running like I want it, is there a way to save every thing in a backup file or an .iso image so that if I need to install it again I don't have to update 100 files agian?

Thanks  Joe

Yes, do a search for a program called "Remastersys"...it's a linux Mint program, but you can install in on Ubuntu no problem. It will create a live CD of your current installation and user data...a perfect backup.

---

### Post by sonofusion82 on 2008-08-11
> **loboc said:**
> look into dd

dd might be the most direct but somewhat raw way to doing it.

i prefer to use clonezilla. it is a free alternative to norton ghost. gparted-clonezilla live-cd is a live CD to create backup and restore harddisk images. [http://gpartedclonz.tuxfamily.org/](http://gpartedclonz.tuxfamily.org/)

---

### Post by robert shearer on 2008-08-11
yes, Remastersys is the one.Make a live cd/dvd of your running system with progs and data that you can use to re-install with.

Good links here...[http://www.remastersys.klikit-linux.com/](http://www.remastersys.klikit-linux.com/)

---

### Post by pparks1 on 2008-08-11
> **bpowell2005 said:**
> Yes, do a search for a program called "Remastersys"...it's a linux Mint program, but you can install in on Ubuntu no problem. It will create a live CD of your current installation and user data...a perfect backup.

Thanks.   Looks like an excellent way to do this.  I'm playing with it right now.   

This thread gave me the nuts and bolts,
[http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html](http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html)

The only thing that changed was the repository address, which is correctly:
# Remastersys
deb [http://www.remastersys.klikit-linux.com/repository](http://www.remastersys.klikit-linux.com/repository) remastersys/


It's stuff like this which really excited me about Linux.  With other OS's, you would find some commercial application to do something cool and then you either have to spend $$'s or obtain illegally.  But with Linux, you just go find it, and do it.   Free of charge.   Gotta love it.

---

### Post by ntu on 2008-08-11
With Gparted you can copy a partition and paste it in an unallocated space on your hard drive. Not sure if you can paste it into another hard drive?

---

### Post by sonofusion82 on 2008-08-11
> **ntu said:**
> With Gparted you can copy a partition and paste it in an unallocated space on your hard drive. Not sure if you can paste it into another hard drive?

well, not gparted, but clonezilla.
i mean both software just come conveniently as a single live-CD

---

### Post by ntu on 2008-08-11
> **sonofusion82 said:**
> well, not gparted, but clonezilla.
i mean both software just come conveniently as a single live-CD
What is more convenient than having Gparted on the Ubuntu live cd? And you can copy partitions with it.

---

### Post by NJ0E on 2008-08-12
Thanks to all ou fyou.  I will look at remaster.

Joe

---

### Post by tekno62 on 2008-08-12
Im looking for something that will make an copy of my hard drive - its a dual boot with windows xp and ubuntu. Its on my laptop and need both for work.  

I wass thinking that if I pop the Hard Drive out of the laptop and connect it to my main desktop ( ubuntu 8.4 ) then I can just make like a bit copy for when I kill my laptop. then I can just copy windows and lunix partitions back over and everything would work,

Would this work?

---

### Post by sonofusion82 on 2008-08-12
> **tekno62 said:**
> Im looking for something that will make an copy of my hard drive - its a dual boot with windows xp and ubuntu. Its on my laptop and need both for work.  

I wass thinking that if I pop the Hard Drive out of the laptop and connect it to my main desktop ( ubuntu 8.4 ) then I can just make like a bit copy for when I kill my laptop. then I can just copy windows and lunix partitions back over and everything would work,

Would this work?

like i suggest earlier, try dd or clonezilla

---

### Post by Rolcol on 2008-08-12
As people have stated, you can use dd to image your hard drive.  It will include everything that's on your hard drive.  (Deleted files, MBR, partition sizes, every single file, etc.).  The command to do this would be something like:```

dd if=/dev/sda of=/media/other/hard/drive.img bs=1M

```
Be careful if you use DD.  If you confuse "if" and "of", you can destroy your data.  Don't save the image to the same hard drive you're duplicating and do it from a live cd.

---

### Post by tekno62 on 2008-08-20
I have a small problem I have downloaded ISO master - Kiso - K3B - K9copy - Remastersys back up and made a clonezilla boot cd. they all have one problem I cant make an ISO from my USB drive. I pulled my Laptop drive out and have it attached to my main comp (Ubuntu 8.04 64 bit)  Anyone able to tell me how to copy the drive it would be great. 


Thanks 
tekno

---

### Post by MarkieB on 2008-08-20
no longer participating in ubuntuforums.org

---

### Post by tekno62 on 2008-08-20
> **MarkieB said:**
> to answer the original question, a simple way is
[https://help.ubuntu.com/community/FeistyUpgradesFreshInstall](https://help.ubuntu.com/community/FeistyUpgradesFreshInstall)
saves burning :) as long as you A. don't mind the time to re-download packages, B. don't mind needing to reset a few settings that aren't stored in your /home partition [hopefully /home has its own partition]

particularly as, occasionally when the system is wrong, it may not be clear precisely when the error crept in, so the most straightforward answer is a reinstall rather than a 'system restore' equivalent..



Sorry everyone - I was not clear. I have a dual boot on my laptop, with XP.thats why I would like to make an ISO. I have to use windows for work. If I end up killing it Im sol.

---

### Post by tekno62 on 2008-08-21
> **tekno62 said:**
> Sorry everyone - I was not clear. I have a dual boot on my laptop, with XP.thats why I would like to make an ISO. I have to use windows for work. If I end up killing it Im sol.

Just like to say thanks - I moved the clonzzilla cd to the laptop and got the image copied over to a usb hard drive.

thanks

---

