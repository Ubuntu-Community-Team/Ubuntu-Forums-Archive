---
title: "Disk0 Out of Disk error"
date: 2013-06-17
forum: New to Ubuntu
---

### Post by GrouchyGaijin on 2013-06-17
Hi Guys,

I have a Dell Inspiron 1520 laptop with Ubuntu 12.04 installed.
I am not dual booting.

Beginning today I started getting an error message that Disk0 is out of disk and to continue I should press enter.

I press enter and the machine seems to boot fine.

I looked about online and most  Disk0 Out of Disk errors seem to relate to grub2 and occur on dual boot machines, which I am not doing.

Does anyone know (or can explain to me) what exactly Disk0 Out of Disk means?
or how I might be able to fix it?

Does it mean that my hard drive is dying?

---

### Post by oldfred on 2013-06-17
Do not think it is a hard disk issue. You can use disks or Disk Utility from Ubuntu and click on drive and verify that drive passes Smart Status. All I really know is green is good, but it can run a lot of tests.

But it may be where grub & kernels are on drive and/or BIOS settings. Is BIOS have drives in AHCI mode not IDE? If no AHCI then is it LBA or large?

Then it may be that new grub or kernel files are further on the drive or beyond 100GB. Some BIOS seem to have issues. And it is not always consistent.

 Out of disk error add to grub install disk-module=ata or use Boot-Repair ATA Disk support
HOWTO: dualboot on big disk (BIOS limitations)
[https://help.ubuntu.com/community/InstallingUbuntuOnBigDisk](https://help.ubuntu.com/community/InstallingUbuntuOnBigDisk)
[http://ubuntuforums.org/showthread.php?t=1998257](http://ubuntuforums.org/showthread.php?t=1998257)

---

### Post by GrouchyGaijin on 2013-06-17
Thank you for the quick answer Fred,

The disk is listed as a 120 GB drive - I'm not sure how to tell if it is set to AHCI mode and not IDE.  I didn't see anything about that on the setup screen when I booted (F2 to bring up setup).

I did the self tests and got conflicting answers.
It said it passed but failed the read test.
See this screen shot:  [http://screencloud.net/img/screenshots/54a05d94cf4adfad7daa164991b48428.png](http://screencloud.net/img/screenshots/54a05d94cf4adfad7daa164991b48428.png) ( #4 is highlighted because I moved the cursor there to make the other entries easier to read.)

I also had a warning as shown in this shot: [http://screencloud.net/img/screenshots/839776329f38bdd9c1881900174e2321.png](http://screencloud.net/img/screenshots/839776329f38bdd9c1881900174e2321.png)

Any ideas?

Thanks again.

---

### Post by oldfred on 2013-06-17
A few bad sectors is normal on many drives. It seems to say drive is ok as overall is green. But if bad sector count starts to grow or grow quickly then you have a failing drive.
Good backups are always the best thing to have. And if drive is giving some warnings it should highlight that you need to have a good backup plan.

       discussion of alternatives/strategy backups
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)

If system is that old then you may not have AHCI. Do you have one large / (root) partition? As that could be where an update put some kernel file beyond the 100GB point on drive, so then you get the out of disk error.

I prefer smaller / (root) of 10 to 25GB and the rest of space as /home or /mnt/data. I use several separte data partitions but they are on other drives also.

---

### Post by GrouchyGaijin on 2013-06-17
This laptop is about 6 years old.
(I'm saving up for a System 76 laptop I plan on getting next time we visit the US.)
I'm not sure why, but I was able to boot normally this morning.

---

### Post by GrouchyGaijin on 2013-06-20
I realized the problem started after I used Ubuntu Tweak's clean up feature.
I reinstalled Ubuntu and the problem is gone.

---

