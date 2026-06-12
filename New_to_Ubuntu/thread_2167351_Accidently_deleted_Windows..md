---
title: "Accidently deleted Windows."
date: 2013-08-13
forum: New to Ubuntu
---

### Post by scottyp2 on 2013-08-13
Well, I've been testing out different kinds of Linux becuase I wanted to switch over from WIndows Vista x62, it's slow and bulky.  I've been dual booting With Ubuntu and trying out other kinds of Linux, and my favorite is xUbuntu.  Long story short, I tried to dual boot xUbuntu and deleted all of WIndows Vista, is it possible to get Vista back?  I have my revocery disk, but I'm not sure about all of it.  Please help!:-?

---

### Post by TheFu on 2013-08-13
You need to have created a backup of Vista in order to recover it. I suspect you are screwed. Sorry.
BTW, backups are important for many, many reasons, but they are especially critical when modifying partition tables. 1 small error, as you have learned, will wipe an entire OS.

If you like pain and didn't write too much xubuntu to the HDD, you might be able to recover some files using **testrec**. It isn't user friendly and doesn't restore with ease.  Best to get a new HDD now and only write things to it - stop using the old HDD except to copy from ... not running an OS on that old HHD would be smart until you've recovered as many files as possible.  BTW, I'd assume all the Vista files were gone just to set your expectations into the real-world.

Use ddrescue to mirror the old HDD onto a new HDD when the time comes. Again - do not write to the old HDD until you have everything off it or give up.
I'd also point out that there are data recovery services available if the data is important. These run $3,000 per drive and up.  I find that having a good backup solution is cheaper.

I realize this isn't what you wanted to hear. Sorry.

---

### Post by DuckHook on 2013-08-13
Hi scottyp2,

Welcome to Ubuntu and the forum. Sorry that your first exposure to the forum has to be a crisis.

@TheFu is absolutely correct in setting your expectations low. Data recovery is very technical and not usually successful unless you are well versed in what you are doing. His reminder to not touch the target HDD is spot on. Every usage of this disk makes the prospect of recovery more remote, and the odds are not great to start with. If you want to try recovery, here are some links that should be helpful:

[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://ubuntuforums.org/showthread.php?t=1958605](http://ubuntuforums.org/showthread.php?t=1958605)

Good Luck! And let us know how it goes.

---

### Post by Roger Cook on 2013-08-13
Are you sure , you may have only fouled up grub?  If you didn't tell it to use the whole disk it is still there, if that is the case if you will download "super grub" you can boot directly into vista with it,

---

### Post by Megaptera on 2013-08-14
> **scottyp2 said:**
> ..... I have my revocery disk, but I'm not sure about all of it.  Please help!:-?

Hi,
Is it  recovery disk you burned yourself when machine was new, or one that was supplied when you bought the machine? Or is it a full-blown Vista o/s disk?

---

