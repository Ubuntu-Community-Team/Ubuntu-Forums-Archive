---
title: "Removing Windows and keeping Ubuntu 11.10"
date: 2012-03-02
forum: New to Ubuntu
---

### Post by tazz4vr on 2012-03-02
Okay, so now that I have been using Ubuntu 11.10 specifically for a few weeks now, which by the way, I totally love it....  anyway, I have it installed along side my Windows OS and would like to change that.  I would like to remove the Windows OS completely. 8-[

I will be further researching the best and safest way to remove Windows from my puter, but would like to know if there are any suggestions/advice out there for me before starting such a task?

---

### Post by VH-BIL on 2012-03-02
You could just format the Windows partition as a EXT4 or what ever partition you like, create a directory on your file system somewhere and edit /etc/fstab to have the drive mounted at boot automatically. (I did it this way)

Or you could use a bootable CD partition application that can delete the windows partition and then resize the Linux partition.

---

### Post by tazz4vr on 2012-03-02
Thank you... total newbie here, so my response would have to be... huh?

---

### Post by Miljet on 2012-03-02
Your title indicates that you installed using wubi, but your first post says that you installed alongside Windows. The procedure would be totally different for each type installation. Before trying anything, you need to make certain how you installed Ubuntu. If you are uncertain, open a terminal and type ```
sudo fdisk -l
```
You will be asked for your password (the same one you use to log in). Your password will not be shown, but just type it in anyway and hit Enter. And b the way, that is a small letter L, not a one.

Copy the results of that command and post it here. Someone will be able to ascertain your installation method.

---

### Post by guilleme on 2012-03-02
Personally, I believe the best way to accomplish what you want, would be to make a LiveCd, boot from it, and install the thing on the whole disk. It is easy, and to install on the whole disk is one of the default opions of the installer, so not much trouble. 
That has a couple of drawbacks: if you installed ubu with wubi, you would loose your files, unless you back them up. If you installed from a LiveCd... not much trouble. 
Pd- If you decide to follow this advice, you can do interesting stuff with partitions, but if you do so, remember to ask for advice before installing.

---

### Post by critin on 2012-03-03
Your title lists Wubi as your version.  It's installed inside Windows as any program is in Windows.  If you delete Windows, you delete ubuntu at the same time.  Download a live CD and do a fresh install using the whole disk or, installing side-by-side windows.  You may wish you'd kept Windows at some point and if your disk is large enough, I'd suggest keeping both.

Is ubuntu listed in your install/remove programs in Windows?  If so, it's a part of Windows.

---

### Post by tazz4vr on 2012-03-06
Sorry for the post and then disappearing for a few days... work matters!  

Thank you for all the responses.  I did install along side Windows, yes, it is listed under the Install/Remove programs.  I apologize for not correctly titling, but I thought when the install was along side Windows, it was Wubi... what the heck is Wubi then?  How do you keep all the different names apart let alone know which one you are using?  Is my version the Ubuntu 11.10 or is there another name for it?

Okay, I agree, I should know about the one I am installing prior to the install, my mistake!  

So, as a total newbie here, would it be best for now, to keep the Windows OS?  If so, what is the best way to make sure that my puter doesn't get bogged down having both, even if I am only using the Ubuntu.

---

### Post by rectec794613 on 2012-03-06
Just droppin in...

I would keep Windows if you have the disk space. Personally, I allocated around 100GB for Windows because I have many games installed. I allocate 20GB for my Ubuntu installs, and it has never been a problem. Other than that, you may wish to keep Windows. You might need it in the future.

And no, having Windows and Ubuntu on the same disk won't bog it down. :)

---

### Post by tazz4vr on 2012-03-06
> **Miljet said:**
> Your title indicates that you installed using wubi, but your first post says that you installed alongside Windows. The procedure would be totally different for each type installation. Before trying anything, you need to make certain how you installed Ubuntu. If you are uncertain, open a terminal and type ```
sudo fdisk -l
```
You will be asked for your password (the same one you use to log in). Your password will not be shown, but just type it in anyway and hit Enter. And b the way, that is a small letter L, not a one.

Copy the results of that command and post it here. Someone will be able to ascertain your installation method.

Here is what came up per the above instructions you provided....

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xa7950ddd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048    20973567    10485760   27  Hidden NTFS WinRE
/dev/sda2   *    20973568   166744063    72885248    7  HPFS/NTFS/exFAT
/dev/sda3       166744116   312575759    72915822    7  HPFS/NTFS/exFAT

---

### Post by Mark Phelps on 2012-03-06
You have no Linux filesystem partitions on the drive, so clearly, you have a Wubi installation -- INSIDE Windows.  You need to follow the links posted earlier about moving the Ubuntu install OUTSIDE Windows if you want to save it.

---

### Post by critin on 2012-03-06
> **tazz4vr said:**
> Sorry for the post and then disappearing for a few days... work matters!  

Thank you for all the responses.  I did install along side Windows, yes, it is listed under the Install/Remove programs.  I apologize for not correctly titling, but I thought when the install was along side Windows, it was Wubi... what the heck is Wubi then?  How do you keep all the different names apart let alone know which one you are using?  Is my version the Ubuntu 11.10 or is there another name for it?

Okay, I agree, I should know about the one I am installing prior to the install, my mistake!  
.

Don't apologize, you did title correctly.  (even if you didn't, there's no need)  It is confusing.

Wubi stands for [COLOR=Red]W[/COLOR]indows [COLOR=Red]ub[/COLOR]untu [COLOR=Red]i[/COLOR]nstaller  It will install many versions to rest [COLOR=Red]inside[/COLOR] Windows.  A Windows Program. 
To install side-by-side, the OS will install in its own partition, but inside the current Windows partition.  So if the current Windows partition is 50 gibs, ubuntu will use a part of that one--you will have both os's sharing that 50 gib partition though they each have separate partitions.  
If the Windows partition is shrunk to 20/25 gibs to make room for ununtu, and the user then choses side-by-side, ubuntu tries to squeeze into the 20/25 gib partition that has again been shrunk to accommodate it.  Not good.

Unallocated or free space will not be used unless you use the 'something else' option and create/designate a new partition inside the unallocated or free space.

You are using unbuntu 11.10.  ;)  Isn't it fantastic?

---

### Post by tazz4vr on 2012-03-06
@critin - Yes, Ubuntu 11.10 is awesome!  I love the opportunity I am provided to use all of the additional resources Ubuntu has to offer, without breaking the bank.  

In regards to the Windows vs Ubuntu decision.  I am pretty sure that I am going to completely remove Windows.  I am in the process of creating a CD.  However the removal task will be handled over the weekend, just incase I mess something up I don't want it to cause issues with my work schedule.

Will keep the updates and questions coming I am sure... thanks to all for the help and suggestions.

---

### Post by kurt18947 on 2012-03-07
> **tazz4vr said:**
> @critin - Yes, Ubuntu 11.10 is awesome!  I love the opportunity I am provided to use all of the additional resources Ubuntu has to offer, without breaking the bank.  

In regards to the Windows vs Ubuntu decision.  I am pretty sure that I am going to completely remove Windows.  I am in the process of creating a CD.  However the removal task will be handled over the weekend, just incase I mess something up I don't want it to cause issues with my work schedule.

Will keep the updates and questions coming I am sure... thanks to all for the help and suggestions.

I would recommend caution about totally removing Windows.  Do you have a means to reinstall Windows if necessary, such as a CD?  You may find yourself with the need to, to example update the firmware on a printer or maps on a GPS.  The only way to accomplish this might well be with Windows, manufacturers don't typically include utilities that run on Linux.  It's a pain but it's also reality for now.

The optimum for me is to have several partitions and a piece of software that enables me to install several operating systems such that each one thinks it's the only one so they don't interfere with one another.  Windows doesn't play well with others.

---

### Post by tazz4vr on 2012-03-07
I do have a computer at my office that is remaining Windows XP as I am sure there are some things/programs that I am bound to Windows for, but the one I use from home, for business as well, is the one that I am looking to convert over to a Windows free system.  If it turns out that I can do everything workwise from my home computer, without issue, then I will consider converting my office computer as well.  My business partner is also interested in this whole task and what it can do for our other business.  The other business deals in a lot of 3D graphics, maps and so forth, so at this time, we are strictly Windows there.

---

### Post by dimsabt on 2012-03-11
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000be969

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       32194   258595840   83  Linux
/dev/sda4   *       32194       38914    53972993    5  Extended
/dev/sda5           32194       38633    51721216   83  Linux
/dev/sda6           38634       38914     2250752   82  Linux swap / Solaris
dimitar@dimitar-HP-620:~$

---

### Post by tazz4vr on 2012-03-11
> **dimsabt said:**
> Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000be969

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       32194   258595840   83  Linux
/dev/sda4   *       32194       38914    53972993    5  Extended
/dev/sda5           32194       38633    51721216   83  Linux
/dev/sda6           38634       38914     2250752   82  Linux swap / Solaris
dimitar@dimitar-HP-620:~$

I have no idea what the above means and/or if it is in reference to anything having to do with my question on whether to remove Windows and keep Ubuntu.

---

