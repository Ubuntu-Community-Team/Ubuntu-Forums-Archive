---
title: "Triple boot XP, Vista, and Ubuntu"
date: 2008-08-21
forum: New to Ubuntu
---

### Post by ElephantGun on 2008-08-21
Hey guys, I recently decided and bought a brand new laptop.

I don't think that drivers for ubuntu are an issue at this point in time, but there are a couple of things I'd like to clarify about booting first.

I have a lot of legitimate software (gasp!) on my vista installed, and it's all backed up using complete system recovery if anything goes wrong.

However, what I need to know is about using GRUB to achieve this triple boot.

I read about using GRUB in a data-only partition, and using the menu.lst file to make it hide and unhide the windows OS's. Is this what I should do, or should I just bear with the loss in computing power and fire up a handful of VMs?

In any case, I'm going to do a bit of experimenting on an external drive with partedmagic, so I might not be able to respond for a couple of hours..

Any help would be greatly appreciated. Thanks!

---

### Post by sayakb on 2008-08-21
Triple boot works just fine with GRUB. Grub will give an option to load the Vista bootloader which will take you to the Vista or XP choice menu.

---

### Post by Thelasko on 2008-08-21
> I read about using GRUB in a data-only partition, and using the menu.lst file to make it hide and unhide the windows OS's. Is this what I should do, or should I just bear with the loss in computing power and fire up a handful of VMs?

I don't know much about that first part.  If you install Windows before Ubuntu, Ubuntu will take care of configuring GRUB for you.  I dual boot Ubuntu and Vista and never mess with the menu.lst file.

Deciding whether or not to run Windows in virtual machines really depends on what you are planning to do in Windows.

---

### Post by cariboo on 2008-08-21
I would suggest trying the livecd before committing to repartitioning your hard drive, just to make sure everything works as expected. Grub is just another boot loader. It resides in the master boot record of the first hard drive. It may have a problem detecting two Windows OS's,
but menu.lst is easy enough to edit, so that all your operating systems are listed.

If you are intending on installing Ubuntu on an external drive, be aware that if done incorrectly you may not be able to boot into any os if the external drive isn't connected. Have a look here:

[http://ubuntuforums.org/showthread.php?t=822264](http://ubuntuforums.org/showthread.php?t=822264)

Jim

---

