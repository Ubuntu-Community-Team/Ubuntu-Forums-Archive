---
title: "Upgrading to 8.04 from Gutsy"
date: 2008-06-19
forum: New to Ubuntu
---

### Post by Pwhdavey on 2008-06-19
Hi

How do I safely/easily upgrade from Ubuntu 7.10 to 8.04 via manual CD?

I currently run both Windows Vista and Ubuntu 7.10 on my laptop and am a dial-up user. I hear that before upgrading, Ubuntu has to become up to date with upgrades downloaded. Is this what I must do, on dial-up, before installing the new distro?

Instructions on how to perform these updates would be welcome. :)

However since my 8.04 has been downloaded and transferred onto CD, when the CD is inserted into the drive there is no automatic upgrade notice and instead it just opens up the files and contents of the CD. 

Thanks!:KS

---

### Post by Sarah L on 2008-06-19
Generally, Ubuntu's software upgrades (including version upgrades) are done through your package manager, which retrieves the files from the Internet. Unfortunately, version upgrades tend to be large and can be unwieldy if you have a dial-up connection.

A liveCD only contains a few basic packages needed for a new installation. Remember, a CD only holds ~700 MB. Some distributions provide a complete software collection on a set of DVDs (I remember downloading 3 DVDs worth of Debian - that's 4.7GB *3!) but that doesn't seem to be the case here.

If you want to upgrade through the liveCD you'll probably have to do a fresh install. Backup your home directory to an external drive and overwrite your 7.10 partition. This is what I did for the 7.10 - 8.04 upgrade. Plus, version upgrades sometimes break your installed software, so it's often easier to start fresh.

However, if you have a laptop, an easier option might simply be to take it to some place with a high-speed internet connection (such as a wireless hotspot or an internet cafe) and do the upgrade through the internet.

---

### Post by Duck2006 on 2008-06-19
After you have updated you may be better to make some rep'o cd or dvd,s.

[http://ubuntuforums.org/showthread.php?t=352460&highlight=updating+off+line](http://ubuntuforums.org/showthread.php?t=352460&highlight=updating+off+line)

---

### Post by avtolle on 2008-06-19
If you are using the Update Manager, yes, you would need to fully update your 7.10 before proceeding. As you are contemplating a "fresh install" from CD, this would not be necessary. You will have a large number of updates once the installation is completed, which may well be awkward on a dial up, so finding (if possible) a high-speed connection would be advised.

---

### Post by kansasnoob on 2008-06-19
Simply as a matter of personal preference I'd "shrink" the existing 7.10 partition using Gparted from your live CD to give up 10 GB of space for your new 8.04 OS. 

That of course assumes that you have enough disc space to do that, but there are definite advantages:

#1. If you hate it you can delete it, edit GRUB, and go back where you were.
#2. You'll be able to use your old OS(s) until you know everything works right.
#3. You'll easily be able to use the live CD and delete whatever partitions you choose to afterwards. (Of course you'll want to plan ahead for GRUB)

NOTE: I've installed as many as three Ubuntu OS's along with XP and the one thing to remember is that the last OS installed will rule GRUB! Sadly, if you remove that "last" OS GRUB does not just "fall back" in place a good soldier. So always work out your GRUB changes before axing any OS! Maybe a separate GRUB partition would work well for you.

---

