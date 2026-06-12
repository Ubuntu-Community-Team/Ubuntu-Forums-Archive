---
title: "Reinstalling XP on a dual-boot HD..."
date: 2012-02-04
forum: New to Ubuntu
---

### Post by ryanryanryan on 2012-02-04
I posted this in the ABSOLUTE BEGINNER TALK forum because I'm an absolute beginner not only with Ubuntu, but with computers as well. 

OK, I need to reinstall Windows XP. On the hard drive where XP resides, I also installed Ubunto 10.10.

Ubuntu works amazing. 

Here's the question - Can I reinstall XP on the same partition it is on now, or do i have to reinstall it on the entire hard drive thus overwriting Ubuntu?

Thanks.

---

### Post by oldfred on 2012-02-04
What XP do you have? 

If it is a full install disk, then you should just be able to reinstall to a primary XP partition that is NTFS formated with the boot flag. If you have moved boot flag, you have to move it back to the NTFS partition.

If you have just a recovery (drive image) disk that usually wants to restore the drive to factory brand new, or it erases everything.

---

### Post by ryanryanryan on 2012-02-04
Thanks for the reply...

i don't have the discs. would have to be from a downloaded ISO image.

So, what you are saying is that a reinstall from an ISO file will erase Ubuntu? If thats the case, once XP is reinstalled, than I would have to repartition the HD to make room for Ubuntu, and reinstall it as well?

Thanks.

---

### Post by ryanryanryan on 2012-02-04
Oh yeah, its xp home edition

---

### Post by Bartender on 2012-02-04
ryanryan -
A Windows install CD won't even see the Linux partitions.  If the ntfs partition is at the front (left side in a graphical view) of the drive, you *should* be able to install Windows to it.

When you say downloaded, doesn't that mean pirated??

Anyway, questions of legality aside, if Windows installs successfully, the problem you'll be facing is that it will rewrite the MBR and you won't be able to boot to Ubuntu.  So you'll have to fix that by reinstalling/repairing GRUB.  I'm not completely familiar with how to do that but there are various tools available.

---

