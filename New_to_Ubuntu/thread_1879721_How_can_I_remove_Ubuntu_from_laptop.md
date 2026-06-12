---
title: "How can I remove Ubuntu from laptop?"
date: 2011-11-12
forum: New to Ubuntu
---

### Post by JohnTho on 2011-11-12
Hi,

I installed Ubuntu 11.04 alonside the existing Windows XP on an Acer Aspire 3500 but now want to remove it. Is there any way to remove the grub boot manager? I've tried using the Acer recovery disks but they just re-install a clean XP system without changing the MBR.

If I can't remove grub can I change the default boot order so that XP is the default?

---

### Post by Gone fishing on 2011-11-12
You can remove grub by using a Windows install CD going to the console and using the fixmbr command [http://helpdeskgeek.com/how-to/fix-mbr-xp-vista/](http://helpdeskgeek.com/how-to/fix-mbr-xp-vista/)

---

### Post by anewguy on 2011-11-12
Or an alternative:

- boot up Windows
- download the free program mbrfix (try downloads.com if you can't find it on the net)
- run mbrfix from a MS-DOS prompt "window" (see accessories).  If you only have a single disk, the syntax would be:

mbrfix /drive 0 fixmbr

This will change the MBR to boot Windows only - no link back to grub.

Now you can boot a livecd, run gparted or the disk manager, delete your Ubuntu partitions.  If the Ubuntu partitions were all after your ntfs partition for Windows, then you can extend the ntfs partition into the newly opened space.  On first boot of Windows after this it will run chkdsk - that's normal.

Dave ;)

---

### Post by BillyBoa on 2011-11-12
Another solution if you don't have the Windows CD is the following:

From Ubuntu software center, download the Startup Manager.

Open it and in Boot options tab, go to Timeout and set it to 0. Go down to Default operating system and choose Windows XP.

Then you reboot and Ubuntu disappears.

If you like to recuperate the space occupied from Ubuntu, use an Ubuntu CD and logon without installation.

Open the program Gparted and from there, delete Ubuntu Swap partition and _VERY CAREFULLY_ only _reduce_ the Ubuntu partition to the minimum. 

[COLOR="Red"]You cannot delete[/COLOR] it because you will lose grub and the system will not boot.

---

### Post by JohnTho on 2011-11-12
Thank you all for your help. On Dave's suggestion I downloaded mbrfix which fixed the mbr ok. I used Windows disk manager to delete the Linux partitions then used gparted from my Ubuntu live CD to extend the relevant Windows partition into the free space.

Everything is now back to original spec, so many thanks for that.

I originally installed Ubuntu on this old laptop because I wanted to play with it independantly from my main PCs. Unfortunately I had a few problems with it on this laptop so I've decided to look for a desktop machine to continue the evaluation. I hope, once I've gained a bit more experience, to make the switch from Windows, although it might not be possible to dispense with it completely, unfortunately.

Once again, thank you all.

---

### Post by anewguy on 2011-11-13
> **BillyBoa said:**
> Another solution if you don't have the Windows CD is the following:

From Ubuntu software center, download the Startup Manager.

Open it and in Boot options tab, go to Timeout and set it to 0. Go down to Default operating system and choose Windows XP.

Then you reboot and Ubuntu disappears.

If you like to recuperate the space occupied from Ubuntu, use an Ubuntu CD and logon without installation.

Open the program Gparted and from there, delete Ubuntu Swap partition and _VERY CAREFULLY_ only _reduce_ the Ubuntu partition to the minimum.

[COLOR="Red"]You cannot delete[/COLOR] it because you will lose grub and the system will not boot.

This is not a good way to try to accomplish this, in fact if you'll excuse me, because everyone appreciates the effort and I don't mean to be disrespectful, but you really don't ever want to do it this way.  All that's needed is to restore the mbr to boot Windows and not use grub, and there are plenty of posts in the forum as well as tools on the net for doing so.  Your way leaves Ubuntu taking some space on the disk because you have to keep grub because you've never update the mbr.

Again, I don't mean to be disrespectful, but considering this is the beginners forum we really don't want to get people off on the wrong foot.  This might leave some thinking that once you've installed Ubuntu there is no way to completely remove it as the OP wants, when in fact it is quite easily done.

Dave ;)

---

### Post by I2k4 on 2011-11-13
> **anewguy said:**
> Or an alternative:

- boot up Windows
- download the free program mbrfix (try downloads.com if you can't find it on the net)
- run mbrfix from a MS-DOS prompt "window" (see accessories).  If you only have a single disk, the syntax would be:

mbrfix /drive 0 fixmbr

This will change the MBR to boot Windows only - no link back to grub.

Now you can boot a livecd, run gparted or the disk manager, delete your Ubuntu partitions.  If the Ubuntu partitions were all after your ntfs partition for Windows, then you can extend the ntfs partition into the newly opened space.  On first boot of Windows after this it will run chkdsk - that's normal.

Dave ;)

I'm finding this an interesting discussion, as I recently dual booted Lubuntu 10.10.  So far so good, I'm very happy with it, but I would really like a "non-destructive" way to return to Windows only, or move on to a different Linux dual boot, down the road.  Up to now I've understood it's necessary to use a Windows disk (which I don't have for my netbook) to fully replace the Linux install.

1) Does your method mean I could completely remove GRUB and delete the partition created for Lubuntu to give it back to Windows, without a Windows disk? (Like most netbook owners, all I have is a Windows "recovery" partition on the hard drive, and no optical disk.)

2) Would this method leave my existing Windows installation, software and files intact, or require reinstalling Windows?

---

### Post by anewguy on 2011-11-13
> **I2k4 said:**
> I'm finding this an interesting discussion, as I recently dual booted Lubuntu 10.10.  So far so good, I'm very happy with it, but I would really like a "non-destructive" way to return to Windows only, or move on to a different Linux dual boot, down the road.  Up to now I've understood it's necessary to use a Windows disk (which I don't have for my netbook) to fully replace the Linux install.

1) Does your method mean I could completely remove GRUB and delete the partition created for Lubuntu to give it back to Windows, without a Windows disk? (Like most netbook owners, all I have is a Windows "recovery" partition on the hard drive, and no optical disk.)

2) Would this method leave my existing Windows installation, software and files intact, or require reinstalling Windows?

Yep - that's exactly what it's for!  EDIT:  By that I mean yes, it sets the mbr for Windows so grub is no longer used (you are free to remove the Ubuntu partitions) and yes, it leaves your existing Windows installation as-is -> it only updates the mbr.  As with anything along these lines, it never hurts ;) to have a good backup.

For anyone interested in an extended discussion on this and other ways to recover, please see the how-to I started:

[http://ubuntuforums.org/showthread.php?t=508927]("http://ubuntuforums.org/showthread.php?t=508927")

Dave ;)

---

### Post by JohnTho on 2011-11-14
I2k4,

I can confirm that Dave's method works. Although my laptop has an optical drive all I have are the recovery disks. See my last post (#5). However as you don't have an optical drive you may need to download and use a Windows-based partition utility such as [Partition Master]("http://www.partition-tool.com/?gclid=CJPi4YbgtawCFcQf4Qodw1c_mg") in order to recover the free space for Windows. I couldn't see any way to use the Windows Disk Management tools to do this, unless anyone knows another way.

Incidentally, I used the GUI version of gparted from the live CD. This allows you to just drag the partition boundaries to where you want and shows the sizes. Then you just click on the execute button and it does it all. I was well impressed with that! :)

---

### Post by anewguy on 2011-11-14
Just glad you got things back to the way you want them!

Dave ;)

---

### Post by I2k4 on 2011-11-14
Thanks to both of you.  The how-to looks very good, though I don't plan to use it for a while.  

It would seem to me no need to be apologetic about posting clean removal instructions - there are so many Linux alternatives that I'd expect a lot of users committed to dual booting will appreciate directions on removing one distro to replace it with another, without damaging the Windows installation.

---

### Post by anewguy on 2011-11-14
Yeah - my entire reason for creating it was so that people who either tried Ubuntu and for the time being decided it wasn't for them, or for people who want to try various distributions and don't have extra disk space or the desire to use a VM.  The entire idea was to make things simple and painless, so that anyone's experience with Ubuntu doesn't have a sour end to it.

Dave ;)

---

### Post by JohnTho on 2011-11-15
It says everything about the ethos behind Linux that it doesn't disturb the Windows installation and allows it to be completely restored with a minimum of fuss, whereas if the rôles are reversed Microsoft will quite happily trash any existing installation.

---

