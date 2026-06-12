---
title: "I LOVE LINUX - need some help though ..."
date: 2008-05-17
forum: New to Ubuntu
---

### Post by Ken 24T on 2008-05-17
It's true .. I *do* love Linux, *mind you*, in my day we used to call it UNIX. 

... *anyho* ...

I have a Dell XPS M1710 laptop that was configured with Windows VISTA Business and I decided to try kubuntu dual-booted.
I have tried various distros in the past and I've decided that kubuntu is the one for me! \\:D/

I have both OS's running, but I really want to blow Windows away and dedicate the entire machine to UNIX (*sorry*, Linux :redface:), using the native Linux filesystem format (ext3?). The trick will be to do this while preserving my current kubuntu installation?

I'm more than happy to have my entire harddrive configured as one partition, if that makes it easier?

```
Disk /dev/sda: 98.5 GB, 98522403840 bytes
255 heads, 63 sectors/track, 11978 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2527a2c7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           6       48163+  de  Dell Utility
/dev/sda2   *           7        5229    41953747+   7  HPFS/NTFS
/dev/sda3            5230       11585    51054570    f  W95 Ext'd (LBA)
/dev/sda4           11586       11977     3148740   db  CP/M / CTOS / ...
/dev/sda5            5230       11585    51054538+   7  HPFS/NTFS

Disk /dev/sdb: 4103 MB, 4103937024 bytes
255 heads, 63 sectors/track, 498 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x85a285a2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         497     3992135+   7  HPFS/NTFS

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x44fdfe06

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      121601   976760001    7  HPFS/NTFS

Disk /dev/sdg: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc19aab1b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdg1               1       30401   244196001    7  HPFS/NTFS
```

I think the solution is going to include gparted, but I'm not familiar (and *very* nervous about) using it, nor have I done anything with UNIX filesystems in years (*and years and years and ...*).

So here's your chance fellow "frail, pale, males" ... who wants to help an old dog learn a new trick or two? 

Cheers, Ken. :guitar:

---

### Post by forestpixie on 2008-05-17
"frail, pale, males" ... tsk tsk tsk there are plenty of the other sort here and you'll likely never know who's what :)

Which one of those do you want to install it to? You've got 4 hdd I think.
If you have raid or anything like that I will have no idea about the installing though.

Yes to gparted or similar I use partedmagic myself, I prefer to do the partitioning seperately prior to even booting the buntu cd.

I would seriuosly consider doing a dualboot though, easy enough to bin win after but it can cause a few hiccups putting it back later.

---

### Post by shifty_powers on 2008-05-17
first of all the gparted livecd will do what you want, but it is of course not without risk. back up any important data before hand.

and with regards to forest pixie, could he not just use virtualbox for the very rrae occassions when winodws has to be used?

---

### Post by forestpixie on 2008-05-17
> could he not just use virtualbox for the very rrae occassions when winodws has to be used

Of course, but I'm just giving options and if the few things that he decides he really needs turn out to need 3d then vbox won't be very much help afaik. 

The most important thing is probably going to be to decide where to put it.

---

### Post by Bakon Jarser on 2008-05-17
Here's a nice guide to using gparted.

[http://gparted.sourceforge.net/larry/generalities/gparted.htm](http://gparted.sourceforge.net/larry/generalities/gparted.htm)

---

### Post by Ken 24T on 2008-05-17
I have attached screen shots of my current HDD configuration.

**snapshot1**: laptop HDD (2 basic partitions) Windows and Linux live on one, sda2 I think and sda5 is for data.

**snapshot2**: USB thumbdrive used for ReadyBoost on Vista

**snapshot3**: USB external drive used for data storage

**snapshot4**: USB external drive also used for data storage

So what I need to do is combine sda2+sda5 whilst preserving my current kubuntu installation. I have been using it now for a month or so an I want to preserve it's configuration.

I would also like to "convert" the NTFS external drives to Linux native format, again without losing any data.

I have no wish to keep my VISTA installation, lord knows I have enough windows platforms @ work to keep me banging my head against the nearest wall!

Again, any help will be appreciated.

Cheers, Ken.

---

### Post by ugm6hr on 2008-05-17
> I have both OS's running, but I really want to blow Windows away and dedicate the entire machine to UNIX (sorry, Linux ), using the native Linux filesystem format (ext3?). The trick will be to do this while preserving my current kubuntu installation?

I'm confused...

I can't see any evidence of a Kubuntu installation.  How did you install it?

If you used Wubi, the process is totally different (and I cant help).

Often, the simplest method is to backup /home and var/cache/apt and then do a fresh re-installation, and start again.

EDIT:
> I would also like to "convert" the NTFS external drives to Linux native format, again without losing any data.
Can't be done, except by backing up data, reformatting, and copying data back.

---

### Post by Ken 24T on 2008-05-17
> **ugm6hr said:**
> I'm confused...

I can't see any evidence of a Kubuntu installation.  How did you install it?

If you used Wubi, the process is totally different (and I cant help).

Often, the simplest method is to backup /home and var/cache/apt and then do a fresh re-installation, and start again.

EDIT:

Can't be done, except by backing up data, reformatting, and copying data back.

I installed it from a PC Magazine-supplied DVD. Initially, I was running it live, but then decided to dual-boot it with Windows. I can see a "ubuntu" folder (see attachment) on my old system drive.

I do notice "wubildr" and "wubildr.mbr". Are these what you mean when you refer to "Wubi"?

If I just backup /home and var/cache/apt to DVD, blow away EVERYTHING, e.g. re-format, re-partition my machine, re-install ubuntu and copy back /home and var/cache/apt ... will that do the trick?

Thanks for the answer on Ext3 conversion ... ;-)

---

### Post by ugm6hr on 2008-05-17
> **Ken 24T said:**
> I installed it from a PC Magazine-supplied DVD. Initially, I was running it live, but then decided to dual-boot it with Windows. I can see a "ubuntu" folder (see attachment) on my old system drive.

I do notice "wubildr" and "wubildr.mbr". Are these what you mean when you refer to "Wubi"?

If I just backup /home and var/cache/apt to DVD, blow away EVERYTHING, e.g. re-format, re-partition my machine, re-install ubuntu and copy back /home and var/cache/apt ... will that do the trick?

Not sure...  I think you have installed using Wubi.  When you installed, did you boot into Windows, and then run the installer?  Or did you boot directly from the DVD to a black screen with the Ubuntu logo and about 5 options (including install)?  The former is Wubi, the latter is a true dual-boot.

As for reinstalling to preserve settings, generally speaking all personalisations are in /home (as are your default document locations etc).  /var/cache/apt/archives is where all the downloaded updates and programs are stored, so restoring them will merely save a bit of internet bandwidth when re-updating after reinstallation.

Can't be certain that *everything* will be preserved because:
1. I don't know what you have done to your system.
2. I don't know where you save your files (most default to /home/username)
3. I think you used Wubi, which changes all the rules.

---

### Post by Ken 24T on 2008-05-17
> **ugm6hr said:**
> Not sure...  I think you have installed using Wubi.  When you installed, did you boot into Windows, and then run the installer?  Or did you boot directly from the DVD to a black screen with the Ubuntu logo and about 5 options (including install)?  The former is Wubi, the latter is a true dual-boot.

As for reinstalling to preserve settings, generally speaking all personalisations are in /home (as are your default document locations etc).  /var/cache/apt/archives is where all the downloaded updates and programs are stored, so restoring them will merely save a bit of internet bandwidth when re-updating after reinstallation.

Can't be certain that *everything* will be preserved because:
1. I don't know what you have done to your system.
2. I don't know where you save your files (most default to /home/username)
3. I think you used Wubi, which changes all the rules.

I think I ran the installer from within Windows.

[LIST=1]
[*]I have 2 users and not many installed apps. I have configured X11 for my graphics card (NVidia) and I have a LCD (external?) monitor using TwinView. I have the usual, e.g., FF bookmarks, TB email configurations, aMule configuration, etc.
[*]I save files to my USB external drive.
[*]I don't understand the implications of using Wubi?
[/LIST]

I'm thinking I should just "bite the bullet" and backup and nuke my machine. Even if I miss some stuff, it's early days and who doesn't enjoy spending the weekend re-building a PC ... come on, *you know you do* ... ;-)

So I guess the next question is, what is the best way to utilize 80Gb of HDD in a ubuntu installation, e.g., how much swap, tmp, home, etc., etc., all one partition or individual partitions???

Cheers, Ken.

---

### Post by mali2297 on 2008-05-17
> **Ken 24T said:**
> 
So I guess the next question is, what is the best way to utilize 80Gb of HDD in a ubuntu installation, e.g., how much swap, tmp, home, etc., etc., all one partition or individual partitions???


In my opinion, two partitions are enough: one main partition for / and a small one for swap. If you want to be able to hibernate the laptop, then the swap partition should be of size at least 1.5 times available RAM.

---

### Post by ugm6hr on 2008-05-17
> **mali2297 said:**
> In my opinion, two partitions are enough: one main partition for / and a small one for swap. If you want to be able to hibernate the laptop, then the swap partition should be of size at least 1.5 times available RAM.

Alternative view here...

3 partitions:
1. **/** around 10GB
2. **/home** around 69GB
3. **swap** around 1GB (or 1.5xRAM if you want to use Hibernate option)

Keeping /home separate makes upgrading in the future without losing customizations easier.  I've only just done this with my laptop when I installed Hardy (after installing Feisty and upgrading to Gutsy).

This might explain it better: [http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

---

### Post by ladr0n on 2008-05-17
> **Ken 24T said:**
> I don't understand the implications of using Wubi?


wubi creates a "fake" ubuntu installation on a drive that has windows installed, which windows sees as one big file on the hard drive.  When you boot into it, it has full control of the computer (unlike a virtual machine) but it is not a full install in the sense that it is installed as real files on a real disk partition.  

I would also suggest using separate / and /home partitions.  I do this myself, and it makes upgrading distros and dual booting my experiment-of-the-week distro (currently arch) with my stable ubuntu install very easy.

---

### Post by Ken 24T on 2008-05-18
Thanks folks ... I appreciate the feedback and suggestions based on real experience are priceless. 

Cheers, Ken.

---

### Post by Ken 24T on 2008-05-24
**IT'S DONE!** :guitar:

I now have a dedicated ubuntu laptop with:

/ 15Gb, /home 75Gb and /swap 3.5Gb 

So far the configuration is going well, I'm just about back to where I was with the exception of getting my gmail account configured properly in evolution?

I LOVE LINUX! 

Cheers, Ken.

---

