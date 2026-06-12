---
title: "Uninstalling GRUB loader from master boot record"
date: 2008-08-24
forum: New to Ubuntu
---

### Post by ThexLeopard on 2008-08-24
Hello,

Today im trying to install the ubuntu server edition for my parents computer, to use as a sort of gate for the internet etc.
I have generic at home and the boot loader installed fine and we basically have the same sort of setup.
At the moment, one drive has XP installed on it (the master) with the secondary device having ubuntu on it (as far as i know its installed correctly).
However the GRUB loader comes up with error 21 when i try to boot up and now i cant access either OS. I tried reinstalling it and even tried installing LILO to get it to boot at least one OS but nothing has worked.

Can anyone help me either repair GRUB so it will boot either XP or ubuntu or uninstall it?

---

### Post by habtool on 2008-08-24
Use a livecd to boot the machine
Then mount the ubuntu partition
then edit /boot/grub/menu.lst
add:
title Microsoft Windows XP Home Edition
root (hd0,0)
savedefault
makeactive
chainloader +1

also from a terminal you can try get grub to install again

[http://ubuntuforums.org/showthread.php?t=24113&highlight=grub](http://ubuntuforums.org/showthread.php?t=24113&highlight=grub)

good luck

---

### Post by habtool on 2008-08-24
One more thing, DONT panic, this is fixable and not a train smash, imo

---

### Post by bumanie on 2008-08-24
If you have a xp disk, go to repair console and do a FIXMBR and FIXBOOT and this will over-write grub and ubuntu will grub will not interfere any more - you can then try the ubuntu server again. Alternatively, you could try super grub disk - a live cd that has good success in reinstalling grub. Error 21 is saying that one of the hdd's is not being recognized correctly in your BIOS settings so you could check them too. Occasionally, hard drive order in BIOS will change for no apparent reason. You have three choices.
1. Check BIOS
2. Try super grub disk
3. Overwrite the MBR via the xp recovery console.
I would tackle them in the above order.

---

