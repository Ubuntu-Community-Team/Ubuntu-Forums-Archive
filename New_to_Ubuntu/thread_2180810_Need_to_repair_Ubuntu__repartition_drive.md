---
title: "Need to repair Ubuntu / repartition drive"
date: 2013-10-14
forum: New to Ubuntu
---

### Post by Queram_Onog on 2013-10-14
God eve gents,

I've recently built myself a new desktop PC with two HDDs, one got Win7 and the other Ubuntu 12.04 (dual boot you call it  I think) - installed from a DVD using wubi - in order to give myself a bit more exposure to Linux. Slowly cracking my way through it, mostly 'doing tutorials' and looking around, no serious work (that's still done on Win) I now need some help:

- Could have I damaged Ubuntu installation with filling up the disk to 100%?
- Could have I damaged Ubuntu installation with hard reset?
- How do I repair Ubuntu installation? (are there more options after 'instal' on the dvd?)
- What's the safest way to repartition the HDD with ubuntu on it?
- Any way to access folders of an ubuntu installation from ubuntu running from dvd?


Bit more info:
An external NAS HDD stopped responding (~400GB data on it) so (after trying everything I could) I pulled it out of its case and mounted it into my desktop pc. Bios sees it as bad drive but both windows and ubuntu could boot up no probs. Win disk mngr could see the disk but win itself could not access it (xfs file sys). So I tried ubuntu the almighty - could see it, access files on it, copy data from it - so I went on to move data from the dying hdd onto linux hdd (home/user/documents). All looking good until ubuntu froze and when it did not recover after ~hour I pressed the reset button (ctrl+alt+del did not work).
After that Ubuntu would take veeeery loooong time to load and would only load in terminal mode (min graphics). After some googling and forum reading, when most of my commands returned 'cannot do, no space left on device' I typed df and found that my linux drive is 100% full though it only occupies ~17GB on 250GB disk. I must have done something wrong when installing, mustn't I?
Dug out ubuntu instal dvd and booted up from there, launched gparted and extended the linux partition to 125GB. Did not help, ubuntu will only make it into terminal mode and after very long time (~1/2hr). So I think I've made myself a new problem...
Anyway, my original problem (dying backup drive) is still here so I am running ubuntu from live dvd and moving data from the dying HDD onto my windows HDD (c/user/docs). Every now and then (2-5min) the process fails (bad hdd not responding) and pc needs to be shut down and started up again (because the bad drive stays invisible/inactive after restart) - pain i.t.a. but so far all data moved appear in good shape. 
But the space is running out on the win hdd - I have plenty more on the linux hdd - but that has a broken ubuntu on it - and I cannot access my folders on it from a livedvd ubuntu.
So, I need to:
a) format the remaining ~half of the linux hdd in windows - not sure I want to do this - this would allow me to use the free space to move the stuff off the dying hdd onto using livedvd ubuntu;
b) access the free space of the linux/ubuntu partition from livedvd ubuntu -  I do not know how to do this;
c) repair the ubuntu installation - I do not know how to do this - perhaps choose install and then there will be further options?
d) with repaired ubuntu installation, re-partition the drive so that all disk is used.
e) get another hdd to temporarily move stuff onto and then do c) and d)

Oh yes, and I also need to get some sleep :)

Any advice welcome

---

### Post by oldfred on 2013-10-14
Never force shutdown unless this this does not work.

 Holding down Alt and SysRq (which is the Print Screen key) while slowly typing REISUB
R-E-I-S-U-B to force shutdown
A good way to remember it is.
Raising Skinny Elephants Is Utterly Boring ...or
Reboot System Even If Ultimately Broken ...LOL.
[http://kember.net/articles/reisub-the-gentle-linux-restart/](http://kember.net/articles/reisub-the-gentle-linux-restart/)
[http://ubuntuforums.org/showthread.php?t=1509765&p=12543274#post12543274](http://ubuntuforums.org/showthread.php?t=1509765&p=12543274#post12543274)

And after a forced shutdown you often have to run fsck if formatted with ext family. Not sure of equivalent for xfs.


 #From liveCD so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

---

### Post by Impavidus on 2013-10-15
You said you used wubi. This makes this system not a true dual boot, as wubi installs Ubuntu in a virtual partition on a windows partition. This is useful when you want to try Ubuntu without repartitioning your drive, but as you want Ubuntu to use one complete drive of your system, with the other drive for Windows, I'd recommend a true dual boot. Actually, I always recommend a true dual boot.

Right now Windows is installed on one drive, whilst the other drive is at least partially formatted as a windows partition, with on it a large file named root.disk, containing the Ubuntu file system. This virtual partition could well be 17GB. The limit is 30GB, reason enough not to use wubi if you want to dedicate a 250GB drive to Ubuntu, besides it being discontinued and not being completely independent from Windows.

It may be useful if you can post a screenshot of gparted showing the layout of your Ubuntu drive, using your live dvd.

To answer your questions:
**- Could have I damaged Ubuntu installation with filling up the disk to 100%?**
I don't think so, but it may make it problematic to boot. Deleting some files to get free space should fix the problem.
**- Could have I damaged Ubuntu installation with hard reset?**
Yes, especially if you were writing to the hard disk (especially system files). Use alt+SysRq+REISUB to reboot an unresponsive system. Only in very rare cases this doesn't work.
**- How do I repair Ubuntu installation? (are there more options after 'instal' on the dvd?)**
Boot from the live dvd, select "Try Ubuntu". There are plenty of tools available, but you have to diagnose the problem before you can solve it. [Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair") can give interesting diagnostics, but I don't think it will be able to solve your problem.
**- What's the safest way to repartition the HDD with ubuntu on it?**
Get your new drive, make backups of your files, wipe and partition the drive using gparted on the live dvd and reinstall. This is much easier and gives a cleaner result than migrating your wubi. When running a live session there is a button the on desktop (used to be at least, haven't tried recently) to install. Install from the live session, not using wubi.
**- Any way to access folders of an ubuntu installation from ubuntu running from dvd?**
Try to find a file called root.disk and mount it as ext4 file system.  That way you should be able to access your wubi Ubuntu from a live dvd.

---

### Post by Queram_Onog on 2013-10-15
Thanks for your attention and bother guys, just quickly tonight:
- managed to move nearly everything from the dying hdd, onto my windows hdd and a borrowed usb hdd; absolute majority is solid and consistent so happy bunny :) (only had to leave some movies behind but that does not worry me)
- ordered new hdd and enclosure to built new external disk (nothing on the market is simple enough for me)
- just out of curiosity, this is what it looks like in disk util, see that often?

[ATTACH=CONFIG]246977[/ATTACH]

The other problem:
- did not know about alt+sysrq+reisub, but neither numlock nor scroll lock lit up the lights on the keyboard, so I doubt reisub would work;
- gparted and disk util screenshots of the linux hdd, from livecd ubuntu session:
[ATTACH=CONFIG]246978[/ATTACH][ATTACH=CONFIG]246979[/ATTACH]
the yellow 17GB section is the original partition, filled up, I then (after the crash) resized it but it did not help the booting; now I also see it's ntfs....... which, as far as I understand things, is not the ideal situation.... wipeout and new instal it is then...
I don't think I have any data of interest on that drive, it'sonly the pain of re-installing some of the softwares... vs the pain of fixing.....

---

### Post by oldfred on 2013-10-15
If it is NTFS, then you must have used wubi.
       [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

Wubi is for a longer term test of Ubuntu over just running liveDVD or flash drive. But one of its main advantages is that you do not have to repartition as it is just a file inside the NTFS partition. It has a max of 30GB, so actual partition size does not really matter much as long as it fits.

Bit more complicated to run fsck on it. Probably should run chkdsk from Windows first.


 [http://ubuntu-with-wubi.blogspot.ca/2011/08/missing-rootdisk.html](http://ubuntu-with-wubi.blogspot.ca/2011/08/missing-rootdisk.html)
sudo mkdir /media/win
sudo mount /dev/sda5 /media/win
sudo fsck /media/win/ubuntu/disks/root.disk
Then check if you can mount it & read it:
sudo mount -o loop /media/win/ubuntu/disks/root.disk /mnt

---

