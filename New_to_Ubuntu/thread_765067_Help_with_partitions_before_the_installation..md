---
title: "Help with partitions before the installation."
date: 2008-04-24
forum: New to Ubuntu
---

### Post by wthoang on 2008-04-24
ok...im currently running the live CD to 7.10...just testing it before 8.04 comes...im new to this...i just ordered the cd a few weeks bak. anywho...wat im wondering is that im using windows...ive got a 60gig harddrive (its an older laptop)...and ive got about 22gigs left. Now is it just as simple as wanting to set up 22gigs for the partition...could i please get a step by step guide? ive searched...but im pretty noob...(im an advanced mac user)

---

### Post by overdrank on 2008-04-24
> **wthoang said:**
> ok...im currently running the live CD to 7.10...just testing it before 8.04 comes...im new to this...i just ordered the cd a few weeks bak. anywho...wat im wondering is that im using windows...ive got a 60gig harddrive (its an older laptop)...and ive got about 22gigs left. Now is it just as simple as wanting to set up 22gigs for the partition...could i please get a step by step guide? ive searched...but im pretty noob...(im an advanced mac user)

HI and welcome, I would like to say yes to being simple but it depends on how many partitions are on the existing drive. You are limited to 4 primary partition to the drive unless you have a extended partition. :KS

---

### Post by wthoang on 2008-04-24
^^^
well...i havent done anything as of yet...ive just been using windows...theres no other partitions set up yet...all im wondering is do i just click...manual once i reach the prepare disk space? ive got the other option of Guided-use entire disk...

EDIT:once ive clicked on manual...i clicked new partition table but it says

You have selected an entire device to partition. If you proceed with creating a new partition table on the device, then all current partitions will be removed.

Note that you will be able to undo this operation later if you wish.

---

### Post by overdrank on 2008-04-24
> **wthoang said:**
> ^^^
well...i havent done anything as of yet...ive just been using windows...theres no other partitions set up yet...all im wondering is do i just click...manual once i reach the prepare disk space? ive got the other option of Guided-use entire disk...

EDIT:once ive clicked on manual...i clicked new partition table but it says

You have selected an entire device to partition. If you proceed with creating a new partition table on the device, then all current partitions will be removed.

Note that you will be able to undo this operation later if you wish.

HI and you may have a look here
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
If you have windows partition then you will have to resize it and you may be able to use the automated install to do that.

---

### Post by bapoumba on 2008-04-24
Moved to its own thread, thanks overdrank :)

---

### Post by overdrank on 2008-04-24
> **bapoumba said:**
> Moved to its own thread, thanks overdrank :)

No thank you  :-\"

---

### Post by kansasnoob on 2008-04-24
I used the following tutorial on my first dual boot with XP already installed and it worked just fine:

[http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm](http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm)

A couple of things I'd recommend: 

(1) Back up anything stored on your hard drive ......... family photos, important documents, basically anything you'd miss if everything goes to the devil. I actually used my Yahoo mail account (I have two addresses that dump to the same inbox) and sent myself a bunch of stuff that I didn't have stored elsewhere in one instance. Other times I've used pen drives, CD's, etc.

(2) Create a new restore point, then clean up all the garbage (temp files, etc.) in Windows and then Defrag! That should make the partitioners job a wee bit quicker.

(3) Read this tutorial completely, if you don't understand anything, ask more questions. I remember being totally dumbfounded about using the "terminal" to make the necessary adjustments to the GRUB menu.

(4) Patience truly is a virtue when it comes to letting the partitioner do it's job. I believe it took about 2 hours for the partitioner to do it's magic reducing an 80Gb XP partition to 40Gb before I could continue installing Gutsy.

Some really great tutorials I've found since then with absolutely fantastic screen shots (but a bit more technical) are right here:

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

Study them all a bit. See what you think your best options are and ask more questions! If you don't get the answer you want start a new thread!

---

