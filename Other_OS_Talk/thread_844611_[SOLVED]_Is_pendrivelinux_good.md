---
title: "[SOLVED] Is pendrivelinux good?"
date: 2008-06-29
forum: Other OS Talk
---

### Post by nerd0795 on 2008-06-29
2 questions:

#1:  Is pendrivelinux good... I'm going on vacation :)  (going to my family in another province)  and they have computers.  I'm getting a 3gig pendrive and I was wondering if Pendrivelinux is a good linux distro, or should I try to put another linux distro on it.

#2 How long do the average (Random thumb drive from staples) last?  I'm going to be away for 2 months.

---

### Post by wolfen69 on 2008-06-30
1. i tried pendrive and thought it was ok, but found ubuntu to work good for me. you might want to have 2 different ways to get your own desktop though. consider using remastersys to make a live cd that is based on *your* desktop. it's awesome to be able to use a live cd that is actually your real desktop. why not do both? if the usb drive install goes bad, you'll have a backup plan at least.

2. i dont think you'll have to worry too much about the live of the flash drive. i believe the # of read/writes is in the millions.

remember, do NOT update the flash install. you can install new apps, but dont update the os. it will kill it.

---

### Post by ironcitypete on 2008-06-30
I think pendrivelinux is based off of mandriva.  I never used it but I have herd some good things about it.

I have fedora 9 on my flash drive. If you have a windows machine you can follow this guide at [lifehacker]("http://lifehacker.com/391067/fedora-9-puts-your-desktop-on-a-usb-drive"). Its a really simple install and works pretty well.

---

### Post by ironcitypete on 2008-06-30
I installed ubuntu using the guide at pendrivelinux.com and the boot time was extremely slow.  Ive herd you can do a regular install of ubuntu on a flash drive and it will work pretty well but i haven't tried it. If you do install ubuntu regularly format the drive ext2 and leave out the swap partition.  That will prevent unneeded reads and writes and extend the life of the flash drive.

---

### Post by wolfen69 on 2008-06-30
after my last post, i installed remastersys and did: sudo remastersys backup and it made a true image of my computer on live cd. (actually live dvd) i rebooted from the dvd and it was exactly like using my regular install. last time i did sudo remastersys dist (which will omit java and some system settings) awesome app. just another option for you in addition to the flash install.

---

### Post by r76 on 2008-06-30
> **nerd0795 said:**
> #2 How long do the average (Random thumb drive from staples) last?  I'm going to be away for 2 months.

:) Any flash drive should last that long.  I'm using puppy and it reads once (at boot) and writes once (at shutdown) - everything else happens in the PC RAM.  So not exactly taxing those read-write cycles. 10,000 cycles should give me about 27 years, using it every day...

The distro depends on what you need for those two months - if it's a vacation do you need the full monty or just internet, email and media player?

---

### Post by lukjad on 2008-06-30
> **r76 said:**
> :) Any flash drive should last that long.  I'm using puppy and it reads once (at boot) and writes once (at shutdown) - everything else happens in the PC RAM.  So not exactly taxing those read-write cycles. 10,000 cycles should give me about 27 years, using it every day...

The distro depends on what you need for those two months - if it's a vacation do you need the full monty or just internet, email and media player?

I have never tried Pendrivelinux so can't comment on it either way. What I can do is give a raving review for Puppy Linux. I'm running an old 633 Celeron with Ubuntu 8.04. While I like Ubuntu I'm having trouble playing movies or DVDs. I just pop Puppy Linux in the drive and I can watch the movies. I can also surf the web, bittorrent (When is the next Ubuntu going to be bittorrented?), write a letter, play a few games, etc. The version I suggest is [TEENpup]("http://linux.softpedia.com/get/System/Operating-Systems/Linux-Distributions/TeenPup-31563.shtml") in my experience simply the best version of Puppy Linux out there.
A few links:

[http://www.puppylinux.org/wiki/archives/old-wikka-wikki/categoryderivative/teenpup](http://www.puppylinux.org/wiki/archives/old-wikka-wikki/categoryderivative/teenpup)

[http://distrowatch.com/table.php?distribution=teenpup](http://distrowatch.com/table.php?distribution=teenpup)

[http://www.murga-linux.com/puppy/viewtopic.php?t=18537](http://www.murga-linux.com/puppy/viewtopic.php?t=18537)

---

### Post by mjwhitfield on 2008-06-30
I've gonna dive right in and suggest you use a disto that is made with the intention of being installed on thumb drive:

[http://www.slax.org/](http://www.slax.org/) - comes with a script for installing to the thumb drive

---

### Post by nerd0795 on 2008-06-30
I'm going to use my 4 GB thumb drive to install fedora.  Since it looks easy.  The 4GB was $20 off costing the cost of a 2GB :)

Thank you for your replies.

---

