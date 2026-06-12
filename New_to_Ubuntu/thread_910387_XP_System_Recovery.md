---
title: "XP System Recovery"
date: 2008-09-04
forum: New to Ubuntu
---

### Post by riowayne on 2008-09-04
I am dual booting ubuntu and Win XP. Lenovo 3000J comp. I need to do a res./recovery to the XP to a date prior to my ubuntu install. If I do the recovery to the XP would that take out the ubuntu? I have to keep the XP so I can use Active X and a couple other programs I can't crossover.

---

### Post by wolfen69 on 2008-09-04
as far as i know, it will wipe the whole drive. no more ubuntu.

---

### Post by tea for one on 2008-09-04
I have never used XP System Restore but I have reinstalled XP from the recovery disk which the user creates when the PC is first purchased.

The recovery disk reinstallation did not wipe the drive completely, the ext 3 (Ubuntu) partition and the Ubuntu installation remained intact.

However XP interfered with the Grub botloader and I had to point Grub to the correct partition with the live Ubuntu CD.

Of course, system restore and reinstallation of XP may be separate functions.

I would be interested to know if they are different?

---

### Post by Mike.B on 2008-09-04
Yes they are. If you re install XP look carefully at all the instructions, because it will allow you to install to the existing directory, which will not interfere with all your files.

---

### Post by LaRoza on 2008-09-04
> **riowayne said:**
> I am dual booting ubuntu and Win XP. Lenovo 3000J comp. I need to do a res./recovery to the XP to a date prior to my ubuntu install. If I do the recovery to the XP would that take out the ubuntu? I have to keep the XP so I can use Active X and a couple other programs I can't crossover.

A system restore (from a restore point) won't cause many problems or any. A full system restore from a partition or a restore disk will likely wipe the entire disk.

---

### Post by Scunge on 2008-09-04
If you're doing a system restore from a saved restore point, rather than a reinstall or restore from a separate backup of XP in its entirety, it will not affect your Ubuntu setup because you didn't install Ubuntu as part of Windows.

All system restore does is copy back a set of system and driver files from a safe place back into your Windows directories. None of this affects your /boot folder on your Ubuntu partition, nor your master boot record.

Similarly, any updates you make in Ubuntu will not be stored as a restore point in Windows, nor will manually setting a restore point save any Ubuntu stuff.
[img]http://i268.photobucket.com/albums/jj22/Rob_0edab8/Spacer.gif[/img]

---

