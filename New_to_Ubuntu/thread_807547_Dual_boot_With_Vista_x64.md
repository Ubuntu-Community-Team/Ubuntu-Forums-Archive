---
title: "Dual boot With Vista x64"
date: 2008-05-25
forum: New to Ubuntu
---

### Post by SP0CK99 on 2008-05-25
Hello all,

I've recently decided to give linux a try and have decided to dual boot with vista (64 bit). I heard Ubuntu was pretty easy to use and decided to go with it.

When I boot form the cd (8.04 64bit) and go the partitioner it sees my c: drive as unallocated, even when i already created a partition for Ubuntu with both Gparted  and Acronis Disk Director.
My C: drive is a 10,000 RPM Western Digital Raptor drive.

When I ran out of ideas i decided use a partition on a different drive. I check the dis for errors and its fine. The ubuntu installer sees this drive just fine. After I set up my /, boot and Swap I proceed with the install, but after it finishes and when I reboot I find that I can't boot to Vista or Ubuntu. To boot to vista I have to use my install disc to repair the Vista installation.

After several attempts and following this tutorial ([http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm))
I have still not met with success.


What on earth am I doing wrong?
Why Does ubuntu see my C: drive as unallocated?

Any suggestion?

Thanks in Advanced,

SPOCK99

---

### Post by wolfen69 on 2008-05-25
did you check your bios to see which drive is booting first?

---

### Post by SP0CK99 on 2008-05-25
I make sure that the drive I install on is booting 1st.

---

### Post by Living2007 on 2008-05-25
> **SP0CK99 said:**
> I make sure that the drive I install on is booting 1st.
I would recommend to boot first from CD.
It is recommended to backup your data before you edit partitions.

EDIT: Ubuntu won't pick-up your Vista drive (C:\ in Windows) because GParted might have caused a crash
Did you get a Pop-up after you edited your partition?

---

### Post by SP0CK99 on 2008-05-25
I keep all my data backed up on an external hardrive.


On my most recent attempt (bout 20 minutes ago) when my machine boot it goes through the motions, checks if needs to boot from cd, and the displayed the word Grub and just sits.

Would this indicate grub failure?


@Living2007

I don't believe I got receive a pop up.
Could this also happen if I'm using Acronis Disk Director?

---

### Post by SP0CK99 on 2008-05-25
I keep all my data backed up on an external hardrive.


On my most recent attempt (bout 20 minutes ago) when my machine boot it goes through the motions, checks if needs to boot from cd, and the displayed the word Grub and just sits.




@Living2007

I don't believe I got receive a pop up.
Could this also happen if I'm using Acronis Disk Director?

---

### Post by Living2007 on 2008-05-25
> **SP0CK99 said:**
> I keep all my data backed up on an external hardrive.


On my most recent attempt (bout 20 minutes ago) when my machine boot it goes through the motions, checks if needs to boot from cd, and the displayed the word Grub and just sits.

Would this indicate grub failure?


@Living2007

I don't believe I got receive a pop up.
Could this also happen if I'm using Acronis Disk Director?
You mean it does nothing, and does not show your multiple OS'.
(GParted is what I recommend for partition editing, don't use anything else)

EDIT: Esspecially in Windows XP

---

### Post by SP0CK99 on 2008-05-25
> **Living2007 said:**
> You mean it does nothing, and does not show your multiple OS'.
(GParted is what I recommend for partition editing, don't use anything else)

EDIT: Esspecially in Windows XP

Exactly.

I tried Gparted but heard that it sometimes didn't play well with vista.

---

### Post by daberger on 2008-05-26
im going to make my usual recomendation and say that u should use wubi the windows based installer. easiest way to linux

---

### Post by meierfra. on 2008-05-26
What is the output of
 ```
sudo fdisk -l
```
(l is a lowercase L)?

You might try testdisk (see my signature) to fix your partition table.

---

### Post by Living2007 on 2008-05-26
OK, grub has failed. Ubuntu needs to be re-installed.

---

### Post by SP0CK99 on 2008-05-26
Reinstall it is then, right after sleep and work :).

---

### Post by meierfra. on 2008-05-26
Different partitioning tools use slightly different conventions to write  a partition table. This can lead to confusion. testdisk (see my signature)  might be able to solve your problem in just a few minute.

---

### Post by Living2007 on 2008-05-26
> **SP0CK99 said:**
> Reinstall it is then, right after sleep and work :).
Ok, this tends to solve 99% of my problems, but I don't use it mush cause my modem isn't compaditle.

Don't uninstall at the first sign of a stuff-up.

---

