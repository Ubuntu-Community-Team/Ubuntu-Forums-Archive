---
title: "motherboard issues"
date: 2008-05-20
forum: New to Ubuntu
---

### Post by j0nes on 2008-05-20
i have a GA-8I945GMF motherboard that worked fine for a few years.  I decided to put Ubuntu on it a few weeks ago.  I did the install, and on the first re-boot i got a blank screen with a cursur flashing in the top left corner just after the bios counted memory and all that.

Now i can't get anything to install or boot.  I've tried my windows disk, Ubuntu (several different versions), Backtrack, Frenzy, and they all do the same thing.  I just get this cursur.

I also tried using my USB keychain that has DSL on it, and i couldn't boot from USB either.

I tried using Windows boot floppys just to see if i could boot from the floppy drive, nothing...

When i power on, the BIOS does it's thing.  If i hit 'del' i can get into the bios and do anything i want in there.  It's as if the bios won't pass things off to a boot loader..

Any suggestions would be greatly appreciated.

I get the same behavior with different (known good) hard drive, RAM, and CD drives and cables.  I've also tried SATA and IDE.

---

### Post by lazyart on 2008-05-20
Flash BIOS and/or load default settings?

---

### Post by j0nes on 2008-05-20
yea i loaded setup defaults and failsafe defaults and got the same results...  My particular BIOS has a few versions F1 through F10.

I had been running F4, so i upgraded to F5, and then to F6.  There was a note on the vendors website saying don't move up more than on version at a time...  ie, don't go from F5 to F9 directly, you must upgrade sequentially.

So the only thing i'm wondering is should i just keep working my way up until i get to F10...

---

### Post by Golem XIV on 2008-05-20
Does the BIOS "see" the drives?  Do they report at POST?  If not, it may be a connection thing - check data and power cables to the drive(s).  If the BIOS sees the drive(s) make sure that the drive geometry is on "autodetect".

---

### Post by j0nes on 2008-05-20
Yes, in all instances and configurations i've tried, the BIOS does report the hard drives, and CD drives.  Everything seems normal until the bios portion of booting is finnished, then i get the cursur.

However, even with one CD Drive and no hard drive, i should still be able to get a live distro to boot.  But i can not.

I know my operating system disks are good because i can get them to boot in other computers.

Does anyone know if a motherboard can 'fail' or be considered 'bad', but still allow you to enter the bios?

Thanks for the help and suggestions thus far.

---

