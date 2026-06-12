---
title: "Re-install of Ubuntu 14.1 - best way to backup?"
date: 2016-01-07
forum: New to Ubuntu
---

### Post by Rion_Zion on 2016-01-07
Hi all, just completed a re-install of my 14.1 ubuntu partition. I've been on ubuntu just over a year now and decided to do a re-install after having some running issues which were mostly if not all created by my own lack of experience in using linux, dodgy manual installs that wen twrong, etc...

now that i have all my packages reinstalled, have latest updates, etc basically everything setup how i want it and running 100% i am wondering what my best course of action would be to have a handy backup of my current system that can be restored, presumably, as a direct replacement for my current ubuntu 14.1 partition 

i'm imagining an iso image might be best, what i'm concerned about is -  would making an iso image of everything in my 14.1 partition (i.e. the bit that is called "computer" in file browser) do the trick and return the OS to its current blissful state, or am i over-simplifying things?

Also, i suppose the iso would have to be restored from outside of ubuntu itself, i have win7 on another partition, would windows be able to restore the iso without any compatibility issues? also would be good to know if this can be done from DOS or grub with a suitable flash drive to load the environment?

i might be barking up the wrong tree so would be open to any alternative suggestions on restoring ubuntu to a pre-defined state without having to go through the rigmarole of a new install ;)

---

### Post by ian-weisser on 2016-01-07
The best backup is one that you find convenient enough to do regularly, and that you can restore from without help.

Bootable-image-based (.iso) backups are possible, but complex. Lots of people do them,
Snapshot-based backups are easy from a VM, but more complex from a bare-metal system. Lots of people do them.
Both have a long-term problem: Ubuntu systems EOL. These backups are locked to a single version of Ubuntu, and cannot be restored to an upgraded system. Someday you will wind up rebuilding your system, and trying to remember all your customizations because you cannot restore them (or easily see them) on the images.

Many oldsters would say you're oversimplifying. They separate your data from system files, and I agree with them.
Many gurus around here use file-based backups (rsync, rdiff-backup) to backup data and a few /etc settings. Ubuntu's default Backup application does this, too. Very easy to restore: Mount the backup disk and copy the files back. Just as easy to restore data and try old settings with an upgraded system.

Most experienced users don't consider the rigamarole of a fresh install to be a barrier. There's a learning curve, and you're on the steep part. Once you are past it, you will see.
Unlike Windows and Mac, reinstalling your favorite packages is usually a single apt command...and many don't even bother doing that, but simply reintall applications as they need them later.


Tip: It's not a backup if you don't do it. And it's not a real, useful backup unless you have practiced restoring from it.

---

### Post by Tadaen_Sylvermane on 2016-01-08
> [COLOR=#000000]i might be barking up the wrong tree so would be open to any alternative suggestions on restoring ubuntu to a pre-defined state without having to go through the rigmarole of a new install[/COLOR]

LVM snapshots is what I would recommend although I have no experience doing it myself. Seems to be what it was made for though. However in the end if Ubuntu 14.1 means Ubuntu 14.10 then you need to re-install to either 14.04 or 15.10. Ubuntu 14.10 is no longer supported. I suggest 14.04 as it will be supported till 2019.

---

### Post by leunam12 on 2016-01-08
Clonezilla. It takes me less than 5 minutes to backup my system partition. Now, I have a fast computer, a small system partition (24GB), and I backup to an internal SATA drive. But it shouldn't take too long to backup to an external drive.

Download a burn clonezilla to a usb stick.
Boot from the USB stick.
I press enter to accept the defaults on keyboard, language, layout, etc.
Start Clonezilla
Device-Image
Local_dev
Select your destination drive or partition (the drive where you are going to be saving to)
Select the folder where you are going to be saving to. (I usually select the root by simply pressing enter).
Accept beginners mode
saveparts (I'm just saving a partition not the whole disk)
Enter a name for your saved image (I do "clonezilla_root_MMDDYYYY")
Select the source partition. highlight the partition, press the space bar to select it and hit enter.
Skip checking the source and the final image (I have never had a problem.)
Press enter
Type "y" and press enter.

Now you have successfully backed up your root partition.

---

