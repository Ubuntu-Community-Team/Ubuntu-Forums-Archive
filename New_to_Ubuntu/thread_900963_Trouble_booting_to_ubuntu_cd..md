---
title: "Trouble booting to ubuntu cd."
date: 2008-08-25
forum: New to Ubuntu
---

### Post by Moroy on 2008-08-25
I had UBUNTU installed as a dual boot with xp on my dell inspiron 1520, (32 bit laptop).  Ubuntu worked nicely for couple weeks.  One day when logging in all I got was an artistic randition of a chicken (no buttons, links, alt+F2 didn't work)  

Anyway, I deleted the ubuntu partition and reformated it to FAT32 using the built in windows xp utility.  I installed the default windows mbr using the xp installation cd.

Finally I set the BIOS boot order to cd/dvd, then to HDD.  Inserted the UBUNTU CD (the same one I used sucessfully before) and when I reboot, xp loads as usuall.  I asume there is some error, and then the boot program decides that trying to boot to the cd/dvd is a bad idea and just goes on to the HDD.  But, I have no idea how to tell what error has occoured.


Any ideas on what the problem could be?

---Edit----
I just installed ubuntu from windows using the live cd.  And when I try to boot to Ubuntu i get the following message:

BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu12) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) _

From here i can enter some commands and they seem to work, but no luck getting into anything resembling ubuntu.

---

### Post by linux6994 on 2008-08-25
The rendition was a heron as in Hardy Heron. Have you tried to wipe off the cd, make sure there are not any finger prints and such. Perhaps even use XP to reburn the cd at the lowest possible speed. Do you have another bootable cd to ensure that the bios will still boot from the cd/dvd burner?

---

### Post by kansasnoob on 2008-08-25
> **Moroy said:**
> I had UBUNTU installed as a dual boot with xp on my dell inspiron 1520, (32 bit laptop).  Ubuntu worked nicely for couple weeks.  One day when logging in all I got was an artistic randition of a chicken (no buttons, links, alt+F2 didn't work)  

Anyway, I deleted the ubuntu partition and reformated it to FAT32 using the built in windows xp utility.  I installed the default windows mbr using the xp installation cd.

Finally I set the BIOS boot order to cd/dvd, then to HDD.  Inserted the UBUNTU CD (the same one I used sucessfully before) and when I reboot, xp loads as usuall.  I asume there is some error, and then the boot program decides that trying to boot to the cd/dvd is a bad idea and just goes on to the HDD.  But, I have no idea how to tell what error has occoured.


Any ideas on what the problem could be?

---Edit----
I just installed ubuntu from windows using the live cd.  And when I try to boot to Ubuntu i get the following message:

BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu12) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) _

From here i can enter some commands and they seem to work, but no luck getting into anything resembling ubuntu.

So you, or someone, got it installed once right? Then things got messed up so you removed Ubuntu and restored Win to it's original state, eh?

Now you've changed things in BIOS and you can't do what was done before???????????

And now it sounds like you're trying to do a Wubi install!!!!!!!!!!!!!

I honestly don't know where to begin!

Can you even run the Live CD?

---

### Post by gaspard.leon on 2008-08-26
On some hardware the live CD won't boot and you get dropped to a busy-box prompt...

I've not been able to use the live CD since Edgy on my hardware (NVidia Nforce 2 Ultra based motherboard with PATA, SATA, and SCSI drives)

However, I got everything going fine using the Alternate install CD...

If you can't boot the CD, it is not going to work... If the CD didn't boot, it's probably not burned correctly or you have the BIOS set to skip the CD and boot straight from the HDD.

The Ubuntu CDs are released in ISO disc image format, which you'll need a program to burn correctly... (from Windows you can use the free program "InfraRecorder" or the non-free Nero or equivalent).

You need to choose the Burn Image option, instead of simply burning the file straight onto the disc.

---

