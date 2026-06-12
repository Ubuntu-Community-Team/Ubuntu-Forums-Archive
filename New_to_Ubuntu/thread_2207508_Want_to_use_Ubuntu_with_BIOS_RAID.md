---
title: "Want to use Ubuntu with BIOS RAID"
date: 2014-02-23
forum: New to Ubuntu
---

### Post by ken18 on 2014-02-23
My system (old Dell Dimension 9100) has built-in RAID (I gather it's called fake-raid from what I've read) and I want to install Ubuntu on a RAID1 pair.  From what I've read, I can either (1) use the BIO settings to create the RAID or (2) use the non-RAID BIOS settings and use software RAID during Ubuntu installation (e.g. alternate CD or server). 

Is there any compelling reason for method (1) vs (2)?  My initial take is that I like (1) a lot because every time my system boots, the BIOS gives me RAID status (e.g. Normal vs Degraded) before the OS actually boots.

I've actually tried #1 and have some problems, but I'll refrain from diving into the details for now.  Appreciate comments on the basic question of method (1) vs (2).

Ken

---

### Post by SeijiSensei on 2014-02-24
Most "fake-RAID" devices rely on a software driver installed at the operating system level. Hardly any of the manufacturers of these devices provide Linux support.  So unless you have a Linux driver in hand already, I don't think you have a choice.  Use software RAID.

---

### Post by ken18 on 2014-02-24
Thanks for your reply.  I've done some digging and it looks like there is some degree of support (see below link), but it's not clear what exactly I need to do.  Software RAID may end up being simpler in the end.  I just wish I could find out what's involved either way so as to make an informed decision.

[http://www.intel.com/support/chipsets/imsm/sb/CS-020663.htm](http://www.intel.com/support/chipsets/imsm/sb/CS-020663.htm)

Ken

---

### Post by SeijiSensei on 2014-02-24
I read that link and the man page for dmraid along with this: [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

Personally if you are not intending on using the device in a dual-boot arrangement, I would choose Linux software RAID.  From my quick scanning of those materials, trying to use fake-raid sounds like more trouble than it's worth.

---

### Post by tgalati4 on 2014-02-24
Why do you want to use RAID?  Why are you rebooting your system?  Whatever you do, upgrade the BIOS to the lastest provided by Dell.  If you are setting this up as a server, then you won't be rebooting often, so the RAID status on boot is a nice feature but won't be used much.  If this is a dual-boot machine, then it might matter.

---

### Post by ken18 on 2014-02-24
Thanks for the additional replies.  I've read the FakeRaidHowTo probably 4 times and can't really make any sense of it.  That's why I'm posting in the Absolute Beginners Section.  To answer other questions, I want to use RAID for data loss protection.  It's a home desktop system (not server) that will be used daily but shut off every night (to save electricity).  Thus, it will be booted every day.  One comment I've read many times that I simply don't get is why RAID is useful for dual boot systems?  I thought the purpose of RAID was performance and/or data loss protection.  I just don't see the connection to dual boot.  I'm leaning more and more toward pure software RAID but before I take the plunge I really would like to know if there are any advantages at all to using the built in BIOS RAID capability (assuming it can be done).

---

### Post by ken18 on 2014-02-25
Just for kicks, I tried creating RAID in the BIOS settings, then installed Ubuntu 12.04 Server using the Manual options, then installed the desktop.  I didn't get any noticeable errors.  Trouble is I have no idea how to tell if everything is ok.  Below is some info I was able to gather.  Any way to tell from the below (fyi, sdc is a separate windows boot drive)?

```
xxxxx@Dell-Dimension-9100:~$ df
Filesystem                           1K-blocks    Used Available Use% Mounted on
/dev/mapper/isw_dhgcjbgjif_Volume0p2 955534076 3604988 903367680   1% /
udev                                    502892       4    502888   1% /dev
tmpfs                                   204720     892    203828   1% /run
none                                      5120       0      5120   0% /run/lock
none                                    511792     152    511640   1% /run/shm

xxxxx@Dell-Dimension-9100:~$ sudo dmsetup ls
isw_dhgcjbgjif_Volume0            (252, 0)
isw_dhgcjbgjif_Volume0p2    (252, 2)
isw_dhgcjbgjif_Volume0p1    (252, 1)

xxxxx@Dell-Dimension-9100:~$ iostat
Linux 3.11.0-17-generic (Dell-Dimension-9100)     02/24/2014     _i686_    (2 CPU)

avg-cpu:  %user   %nice %system %iowait  %steal   %idle
          10.29    3.55    4.17   13.05    0.00   68.94

Device:            tps    kB_read/s    kB_wrtn/s    kB_read    kB_wrtn
sda             211.34     89887.46      1477.70   84942753    1396408
sdb             178.71         1.71     89850.06       1620   84907408
sdc              12.31       601.97         0.00     568854          0
dm-0             89.64       685.76      1477.70     648041    1396408
dm-1              0.58         1.95         0.37       1840        352
dm-2             88.31       683.64      1477.32     646037    1396056

xxxxx@Dell-Dimension-9100:~$ sudo fdisk -l /dev/sda
Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
Disk identifier: 0x0002e3e7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048    11718655     5858304   82  Linux swap / Solaris
/dev/sda2   *    11718656  1953519615   970900480   83  Linux

xxxxx@Dell-Dimension-9100:~$ sudo fdisk -l /dev/sdb
Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
Disk identifier: 0x0002e3e7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048    11718655     5858304   82  Linux swap / Solaris
/dev/sdb2   *    11718656  1953519615   970900480   83  Linux

xxxxx@Dell-Dimension-9100:~$ sudo dmraid -r
/dev/sdc: hpt45x, "hpt45x_SPARE", spare, ok, 488281239 sectors, data@ 0
/dev/sdb: isw, "isw_dhgcjbgjif", GROUP, ok, 1953525166 sectors, data@ 0
/dev/sda: isw, "isw_dhgcjbgjif", GROUP, ok, 1953525166 sectors, data@ 0
```

---

### Post by SeijiSensei on 2014-02-25
On servers with real hardware RAID, you'll see just one device, /dev/sda say, and not the underlying devices like I see here.  Apparently you also chose to use LVM which makes it a bit more difficult to determine what is happening.  I have a sense that Ubuntu ignored the RAID device and installed everything to /dev/sda.  

Also remember that RAID is not a replacement for backups.  RAID1 is less vulnerable to disaster than something like RAID5 where no single drive contains a complete copy of the information.  I've found that I could remove one of the drives from a software RAID1 array and mount it as a regular device.  Still you should set up a regular backup procedure and not rely on RAID.

---

### Post by Vladlenin5000 on 2014-02-25
The BIOS RAID of the Dell Dimension 9100 is managed by a Intel® Matrix Storage Technology which is OS independent. Should be a key combination to bring up the RAID manager during post; create the array. Then, for installing Windows* a driver is required (provided by Dell, Intel, etc.) otherwise it won't see your array; Linux has native support.

It should be this simple.

[http://www.intel.com/support/pt/mt/mt_win.htm](http://www.intel.com/support/pt/mt/mt_win.htm)

* XP/2003; Vista already supported a few; most are supported in 7/8.

---

### Post by ken18 on 2014-02-25
Thanks for the comments.  I think I'll try a pure Software RAID install tonight just to see the difference.  So far I've yet to find explicit instructions on how to do a BIOS RAID install, whereas I have detailed instructions on Software RAID.

SeijiSensei, I'll also incorporate a regular backup scheme.

Vladlenin5000, the link you posted doesn't go anywhere.

Regards,  Ken

---

### Post by tgalati4 on 2014-02-25
Real hardware RAID allows neat things like hot swap.  If you have a failed or degraded drive, on the next boot, you can pull out the drive (while booted into RAID BIOS, typically Control-S on boot), put in a new drive and watch (and wait) while the new drive gets striped into the array.  Once it has checked out, then you can boot normally.  Hardware RAID is helpful for dual boot because the RAID pool appears as one drive to each OS.  With software RAID, you have to install and manage a software RAID manager on each OS and they may not be compatible.  This only matters if you need to share the same data pool between both operating systems.  Hardware RAID can be faster than software RAID depending on your CPU and memory architecture.

---

### Post by Vladlenin5000 on 2014-02-25
Whilst CTRL+S is indeed typical, the Intel Matrix present in the Dell Dimension 9100 uses CTRL+I to access the RAID manager. When in the manager it should be easy provided the user knows what RAID level to choose and select the drives accordingly.

---

### Post by ken18 on 2014-02-25
I'm familiar with using the RAID BIOS settings via Ctrl-I.  I used the system for 8 years in RAID 1 mode with windows XP.  I think maybe twice during that period, it booted under degraded mode and all I had to do was hot swap the failed drive and the system went immediately into rebuld mode and after some time was back to normal.  Now I'm trying to do the exact same thing with Ubuntu but am unsure how to accomplish that.  Here is what I've done so far:

(1) set up RAID 1 in system BIOS (no problem, have done it before on this system).

(2) tried installing the standard Ubuntu Desktop distribution.  The install seemed to work, but the system would not boot.  I tried disconnecting one of the drives and it booted (BIOS showed 'degraded mode' which makes sense).  After booting, I hot connected the drive back in and was able to restart after that (BIOS showed REBUILD status which made sense).  The BIOS never got out of REBUILD status after several hours, which should have been plenty of time for the rebuild.  Also, after some checks, the swap partition was showing as bootable instead of the ext4 partition, yet I don't recall any options in the standard disti to choose which partition was bootable.  I thus concluded something was wrong and decided to try installing the server version instead (because I couldn't find the 'alternative desktop download' that made any sense to me).

(3) tried installed the server version (manual partitioning) where just one device (volume0) was listed on the screen (which made sense to me because I'd already set up the RAID in BIOS).  During the install (manual partitioning) I divided volume0 into a swap partition and an ext4 (bootable) partition.  The install proceeded without apparent error and rebooted OK when the install was complete.  I next installed Ubuntu-desktop.  Trouble I had at that point was determining if everything worked OK, thus my post earlier in this thread with the info I'd gathered.  Based on SeijiSensei's comment ("I have a sense that Ubuntu ignored the  RAID device and installed everything to /dev/sda", I concluded something must still be wrong.

Thus my big question is: "how can one tell if the RAID is set up properly?"  When I looked at the devices with gparted, the volume0 looked ok but said the partition was 'unknown'.  When I looked at sda and sdb, both had red exclamation points and the detail said they weren't mounted.  I don't know if this is normal (because of the BIOS RAID) or something is indeed wrong.  I'm basically stuck not knowing if the install went OK or not.

For two reasons: (1) I have no instructions at all how to install Ubuntu with BIOS RAID and (2) I have no way to determine if the install was done correctly and everything is ok, I thought I'd take a stab at pure Software RAID instead (because I do have explicit instructions on how to do that).  I'd really like to use the BIOS RAID since it is built in to the system, but thus far I have no means to tell if what was done is correct.

---

### Post by CharlesA on 2014-02-25
I would go with software (mdadm/dmraid/whatever) over fakeraid (biosraid) any day because of the lack of management applications.

I think the main problem you are running into is because the system manufacturer probably has a utility to manage the RAID volume in Windows, but doesn't provide a utility for Linux.

I would go with mdadm: [http://zackreed.me/articles/38-software-raid-5-in-debian-with-mdadm](http://zackreed.me/articles/38-software-raid-5-in-debian-with-mdadm)

Same instructions can work for RAID1 with minor modifications.

---

### Post by ken18 on 2014-02-25
Thanks for your reply.  I know for sure there is an app in windows because I saw it on occasion (especially when the RAID was in degraded mode).  My guess is the app did the monitoring/rebuilding and reporting to the BIOS (e.g. rebuild complete to clear the BIOS degraded flag).  I dug around and found the following Intel website:

[http://www.intel.com/support/chipsets/imsm/sb/CS-020663.htm](http://www.intel.com/support/chipsets/imsm/sb/CS-020663.htm)

that implies the BIOS RAID will work in linux but only provides references to dmraid and mdadm w/o any instructions as to what actually to do.  Even if what I've done so far is indeed correct (wish I knew how to tell), my guess is there is more I need to do with dmraid and / or mdadm, but I don't know what that would be.

---

### Post by CharlesA on 2014-02-25
It's like they are telling you to use mdadm or dmraid, but not telling you how you are supposed to set it up.

I'd just forget the fakeraid and run mdadm by itself.

---

### Post by tgalati4 on 2014-02-26
How did you set up your swap partition?  One method would be to set up swap partitions on each drive of the same size then apply RAID0 across the OS partitions but leave the swap partitions out of the RAID and set them manually within linux.  I don't know what the performance hit would be using the drives in this fashion.  With Windows, the entire drive is used in RAID.  No recovery partition, no swap partition, no hidden utilities partition.  Normally in linux you would have a single OS disk with a swap partition and a data disk using RAID.  You can afford to lose the OS because you can reinstall it in 20 minutes with a decent snapshot.  The data is then somewhat protected using the RAID mirror.  Remember, RAID is not a backup strategy.

---

### Post by ken18 on 2014-02-26
Here is what I did:

(1) used BIOS settings to create RAID1 volume from two 1TB disk drives.  Result was a single RAID volume called volume0.

(2) installed Ubuntu Server 12.04 using <manual> partitioning.  Selected volume0 and created two partitions, 
   (a) 6GB, primary, boot flag = no, use = swap, no mount point
   (b) rest of volume0, primary, boot flag = yes, use = ext4, mount point = /
Then the OS installed without apparent error.

(3) OS would not boot after the install. So, I tried disconnecting one of the devices and the system booted (BIOS showed DEGRADED status).  After booting completed, I reconnected the device previously disconnected and the system was able to boot thereafter (BIOS showed REBUILD status).

My guess is that everything worked ok, but I somehow need to manually perform the rebuild.  In windows, there was an app running in the background that would perform the rebuild automatically and change the BIOS status to NORMAL.  I'm guessing that no such app exists in Linux and that the rebuild operations have to be done manually (except I don't know how to do it).  I also don't know how the BIOS will know the rebuild completed and change its status from REBUILD to NORMAL. 

Too many unknowns and I haven't so far been able to find any instructions I can understand.

Ken

---

### Post by ken18 on 2014-02-27
I finally found some useful information in the following thread:

[http://ubuntuforums.org/showthread.php?t=1586099&page=2](http://ubuntuforums.org/showthread.php?t=1586099&page=2)

And especially the following link:

[http://techie.org/Blog/2010/09/03/how-to-rebuild-intel-raid-isw-on-linux/](http://techie.org/Blog/2010/09/03/how-to-rebuild-intel-raid-isw-on-linux/)

Thus, it appears there is a way to monitor and rebuild RAID when using the BIOS RAID settings.  However I found the following comment at the end of the first thread:

> dmraid is not a well tested or supported tool.  It is only provided for  those who need to dual boot with Windows, since Windows does not  understand Linux software raid, and Linux does not understand Windows  software raid.
mdadm Linux software raid is far better tested and supported.  You will  have much fewer problems with it, and it also will resync much faster  when you plug the missing drive back in, so you should use that instead  of dmraid.  It also can do things like add a third disk later on if you  want, which you can not do with the fake raid stuff

Is it still true now (almost 4 years later) that dmraid is considered not well tested or supported and is inferior to mdadm?

Ken

---

### Post by ken18 on 2014-02-28
Here is a nice Intel paper I found through my diggings:

[http://www.intel.com/content/dam/www/public/us/en/documents/white-papers/rst-linux-paper.pdf](http://www.intel.com/content/dam/www/public/us/en/documents/white-papers/rst-linux-paper.pdf)

What I don't quite follow is how to install Ubuntu on the RAID once it's created.  I assume the RAID setup has to be done via LiveCD.

Ken

---

