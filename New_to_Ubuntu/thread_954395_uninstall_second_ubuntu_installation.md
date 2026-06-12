---
title: "uninstall second ubuntu installation"
date: 2008-10-21
forum: New to Ubuntu
---

### Post by cleftonsidney on 2008-10-21
Very new to Linux!! When I changed some video settings, Ubuntu booted to an unreadable screen. To attempt to repair this , I installed a new installation of Ubuntu, to a second partition.
Eventually, I was able to repair the original installation, but now when booting, grub asks which installation I want to boot from.
Can I just delete the new partition that was established with the second installation, (was it "filesystem"  or the balance of the hdd, "29gb media") or is there a way to uninstall the later installation so I don't have to select the installation I want to run every time at bootup?
Cleftonsidney

---

### Post by Bölvaður on 2008-10-21
/boot/grub/menu.lst

check out this file. It is the screen when you pick which ubuntu you use.

You can edit this file anyway you want, including shortening the timer to 1 second or 0 if you will.


So what you could do is delate the partition with the ubuntu you dont want, and just edit grub on the partition that is left on the hdd.
If grub doesnt load and no os at all, then you can restore grub with a cd you can download and burn: super grub disk

---

### Post by wizard10000 on 2008-10-21
> **cleftonsidney said:**
> Very new to Linux!! When I changed some video settings, Ubuntu booted to an unreadable screen. To attempt to repair this , I installed a new installation of Ubuntu, to a second partition.
Eventually, I was able to repair the original installation, but now when booting, grub asks which installation I want to boot from.
Can I just delete the new partition that was established with the second installation, (was it "filesystem"  or the balance of the hdd, "29gb media") or is there a way to uninstall the later installation so I don't have to select the installation I want to run every time at bootup?

Easy to do.

1.  Hit Alt+F2

2.  In the run box, type 'gksu gedit /boot/grub/menu.lst' (no quotes) and hit the OK button.  You'll be prompted for your password.

3.  Comment out the entry for the installation you no longer want to appear on the boot menu by adding a '#' before each line in the entry.

4.  Reboot.  Enjoy.

5.  Once you're sure you've removed the right entry you can go back into menu.lst and remove the entry - or if it's broken now you can replace it with the original file - which will be a hidden file named menu.lst~

After that all you have to do is delete the partition you don't need.

Good luck -

---

