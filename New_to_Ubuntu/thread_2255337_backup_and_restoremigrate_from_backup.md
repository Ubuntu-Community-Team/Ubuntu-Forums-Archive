---
title: "backup and restore/migrate from backup"
date: 2014-12-04
forum: New to Ubuntu
---

### Post by Dragonfly_11 on 2014-12-04
Hi all!

I have a question for you, thank you in advance!

I installed Ubuntu 14.04.01 Trusty on a PC. Now I need to install it to a MacBook Pro (because I need different hardware specs).
As I have already done many installations that took me very long time, I would like to backup Ubuntu from the PC and restore that backup on Ubuntu on Mac.
Is there a way to do that? I mean to use an external hard drive.
I usually use Mac OS X and with it I can either choose to restore from backup or to migrate user data and applications. Is there something similar?

Thank you very much!

Dragonfly

---

### Post by Mark Phelps on 2014-12-04
There are several ways to do this, of which I have personally used two.

1) Clonezilla -- creates an image backup in a folder you choose on the drive you choose,  Primitive text-mode interface, nonintuitive enter-destination-first interface, but very powerful and fast.  Includes option to verify the backup after made to confirm its integrity.

2) RedoBackup -- also creates an image backup in a folder you choose on the drive you choose.  More modern graphical interface, more intuitive but not so flexible.  Have had this simply refuse to work on some distros and versions with no indication why.  But, works OK with Mint 17 and Ubuntu 14.04.

There are others options that other folks will recommend -- but if RedoBackup works for you, that's the one I would use.

---

