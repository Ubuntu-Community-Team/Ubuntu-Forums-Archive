---
title: "Best Format for External Drive?"
date: 2008-05-15
forum: New to Ubuntu
---

### Post by anthropoidster on 2008-05-15
I had a iOmega 160GB External via USB Hard Drive which I formatted ext3 and used as a backup of my Internal 160GB Hard Drive, but which completely disappeared after only two weeks.  Wouldn't show in Gutsy, Feisty or XP on Desktop or Laptop.  Today, fortunately, the dealer replaced it with a new one (they couldn't access it or figure it out).  It was always plugged in but rarely mounted.  Interestingly, I've have a similar problem with a 4GB USB Flash Drive which I also formatted ext3 and which is no longer mounting either.  I'm wondering if using ext3 contributed to my problem or if it's the best (safe, stable) format for back-up.  So my question is, what format should I use for the new External Hard Drive (keeping a full back-up copy of my Internal Hard Drive) and the Flash Drive (keeping a often changing sync copy of active files) and keeping in mind that the original files are on an ext3 partition?  

Meanwhile, the new 160 is staying in the box until I hear some of that great wisdom that has in the past been so helpful.

Thanks...

---

### Post by jimv on 2008-05-15
Personally, I'd go with a FAT32 filesystem, as that will show up on any OS...Linux, Windows, Mac, etc.

---

### Post by vishzilla on 2008-05-15
Fat32 should do as jimv says. Readable in most OSes

---

### Post by herbster on 2008-05-15
If you use ext3 or any other linux filesystem, you just need to install the FS driver on a Windows machine (fs-driver.org) and you can read it just fine.

FAT32 is a safe bet, but of course remember the 4gb file size limitation.

---

### Post by HotShotDJ on 2008-05-15
> **jimv said:**
> Personally, I'd go with a FAT32 filesystem, as that will show up on any OS...Linux, Windows, Mac, etc.On a drive of that size, FAT32 is probably not a very good idea... additionally, FAT cannot properly recover from an improper removal of the device.  If you will only be using the drive in linux, use ext3.  Otherwise, I suggest NTFS for this drive.  Most modern Linux systems have robust support for NTFS and, like ext3, it is a journaled file system which will give you protection against improper removal/shutdown.

---

### Post by az on 2008-05-15
It depends on your needs.

If you need interoperability, vfat is everywhere but has limitations as mentioned.  You can get any OS to recognize ntfs or ext3, but it may require a little work in some cases.  

Regardless of what you pick, your choice of filesystem should not affect the reliablilty of your hardware.  In other words, I think your hardware would have given your problems even if you kept the fat filesystem on it.

---

### Post by bouta on 2008-05-15
and why isn ntfs safe ? i prefer ntfs..for copying large files.btw thanks for the tip concercing ext3 driver for windows

---

### Post by Paqman on 2008-05-15
FAT32 is a terrible filesystem. Tons of fragmentation, no support for large file sizes, etc.

It used to be the recommended format for shared data, but that was before we had NTFS write support for Linux. It's true Macs still only mount NTFS as read-only by default, but the are [NTFS tools for OS X](http://www.tuaw.com/2007/11/19/ntfs-on-your-mac-two-ways/) available.

FAT32 is obsolete, and rapidly moving towards the dustbin of history.

---

### Post by HotShotDJ on 2008-05-15
> **bouta said:**
> and why isn ntfs safeWho said NTFS isn't safe?  It is proprietary and patented, which is enough for many people to steer clear of it.  But on modern Linux systems, it is perfectly safe.

---

### Post by anthropoidster on 2008-05-15
Hey, thanks for your thoughts guys...

Just to make it clear... I would only be using these for back-up of my desktop and not for moving between machines. Both desktop (gutsy, fiesty, xp) and laptop (fiesty, xp) have the ext2 read/write program installed on the xp side (and works great) but I rarely use that side. My first thought was to use ext3 as I did, but it just seems weird that a two week old drive and a not so old flash have both become unmountable with ext3.

My primary need is safe, secure and stable protection of data in an Ubuntu environment.

Thanks again.

---

### Post by capink on 2008-05-15
If you are backing up system files, you will need a filesystem that can store unix permissions as well as ownership. Of all the unix filesystems, the most stable and reliable would be ext3 because of extensive testing and active maintainance. I personally use ext2 for backup drives, as I only need journaling for my internal hdd which is subject to cold reboots and system hangup.

---

