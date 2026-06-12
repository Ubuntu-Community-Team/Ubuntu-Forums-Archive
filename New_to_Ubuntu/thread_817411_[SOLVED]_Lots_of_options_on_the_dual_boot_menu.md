---
title: "[SOLVED] Lots of options on the dual boot menu"
date: 2008-06-03
forum: New to Ubuntu
---

### Post by Modnar1 on 2008-06-03
i was wondering if there is anyway to reduce the number of boot options on from the dual-boot menu screen as i am currently dual-booting windows xp home and xubuntu, however it seems that every time i update linux another two entries get added to the list, so i now have the options: Xubuntu 8.18, Xubuntu 8.18 (recovery mode), Xubuntu 8.17, Xubuntu 8.17 (recovery mode), Xubuntu 8.16, Xubuntu 8.16 (recovery mode) and finally windows xp home. so basically what i'm trying to ask is, is there anyway of reducing that list so that i just get the option for the latest Xubuntu, its recovery mode and windows

---

### Post by Inxsible on 2008-06-03
> **Modnar1 said:**
> i was wondering if there is anyway to reduce the number of boot options on from the dual-boot menu screen as i am currently dual-booting windows xp home and xubuntu, however it seems that every time i update linux another two entries get added to the list, so i now have the options: Xubuntu 8.18, Xubuntu 8.18 (recovery mode), Xubuntu 8.17, Xubuntu 8.17 (recovery mode), Xubuntu 8.16, Xubuntu 8.16 (recovery mode) and finally windows xp home. so basically what i'm trying to ask is, is there anyway of reducing that list so that i just get the option for the latest Xubuntu, its recovery mode and windows
There will not be a 8.16 or 8.17 versions of Xubuntu EVER. because the months 16 and 17 do not exist :)

Anyway, I know what the issue is....you probably mean the kernel number.

You can do 1 of 2 things depending on what you are comfortable with:
1) you can search for the older kernel in Synaptic and remove the older ones - their version number should be listed when you go and search in synaptic. Make sure you only delete the older ones.. AND MAKE SURE you do not remove all of them. This will get rid of the older kernels from the system and the grub menu as well.


2)You can remove the entries from the grub menu without un-installing them. This option is preferred, if you are having problems of any sort with the latest kernel. You can do this by editing this file ```
gksudo mousepad /boot/grub/menu.lst
``` Comment (#)the entries that you dont want - again make sure you keep the newest one around. Save the file and then reboot.

Lastly, if you are not having problems with the latest kernels, then I would suggest you use the first option and actually uninstall the older kernels to clean it up a little.

---

### Post by TeoBigusGeekus on 2008-06-03
```
gksudo /boot/grub/menu.lst
```

Comment out the 8.16 entries (add # in front of them), but not the 8.17 ones, in case something goes wrong in the latest kernel and you need to switch to an older one.
Save the file and reboot...

---

### Post by Rocket2DMn on 2008-06-03
These are mostly older kernels which are useful to keep around in case something fails with the newest kernel.  The posts above show adequate methods of removing them, but I would just leave them there if they aren't TOO terribly annoying to you.

---

### Post by Modnar1 on 2008-06-03
thank you all for your quick replies, i think i will leave the entries there for now unless there becomes too many of them as its only a mild annoyance as my windows entry is at the bottom

---

### Post by meierfra. on 2008-06-04
Change "#howmany=all" in menu.lst  to "#howmany=2" and you will never have more than two sets of kernels.

---

