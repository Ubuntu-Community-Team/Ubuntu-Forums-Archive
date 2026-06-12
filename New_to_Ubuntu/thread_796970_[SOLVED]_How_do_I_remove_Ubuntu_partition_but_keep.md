---
title: "[SOLVED] How do I remove Ubuntu partition but keep GRUB and Vista?"
date: 2008-05-16
forum: New to Ubuntu
---

### Post by some_random_noob on 2008-05-16
(Before anyone asks: I'm doing it for someone else :P )

... so anyway, how do I remove Ubuntu without deleting the bootloader? If I remove Ubuntu, won't that delete GRUB, and therefore screw up the ability to load vista??


**Update: Thanks for the advice everyone. I should be able to do it from here.**

---

### Post by rlcomstock3 on 2008-05-16
This is tricky, I have done this before, you will need to delete the partition then have a windows cd handy, you can then boot the cd, get into a terminal and there is a fix the master boot partition command (google it because I cannot remember what it is or how to get to the terminal).  Then I would recommend booting the ubuntu live cd and using gparted to map the remainder of the harddrive to windows.  I hope that gets you started.  Good luck.

---

### Post by Raccoon1400 on 2008-05-16
You can't keep grub. The config files are on the ubuntu partition. If you had a seperate /boot partition, maybe you could.

to remove ubuntu, but not vista:
In the windows partition manager, delete the ubuntu partition
boot your vista install dvd. Go to the repair your computer section. Open a prompt.
Type /fixboot/mbr.
or is it fixboot/mbr?
try both.

---

### Post by forrestcupp on 2008-05-16
If those commands don't work, try the [Super Grub disk](http://supergrub.forjamari.linex.org/).  It has an option to restore the Windows boot loader.  That worked for me once when I couldn't get anything else to work.

---

### Post by zvacet on 2008-05-17
Read [this]("http://ubuntuforums.org/showthread.php?t=740221") and see if it is helpful to you.

---

