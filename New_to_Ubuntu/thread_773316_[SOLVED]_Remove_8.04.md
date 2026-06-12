---
title: "[SOLVED] Remove 8.04"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by indiana_crook on 2008-04-28
Okay guys, I got one for ya.  I upgraded to ubuntu 8.04 last weekend.  Not a great success.  I went ahead and installed back to 7.10, however all this did was dual boot 7.10 and 8.04.  Can I remove 8.04???

---

### Post by ALex! on 2008-04-28
> **indiana_crook said:**
> Okay guys, I got one for ya.  I upgraded to ubuntu 8.04 last weekend.  Not a great success.  I went ahead and installed back to 7.10, however all this did was dual boot 7.10 and 8.04.  Can I remove 8.04???

make a clean install via a livecd! when asked about partitions, select the "Use complete drive" option....

or... are you dual booting with any other OS???

---

### Post by Tatty on 2008-04-28
Boot into a live cd then load gparted (System->Administration->Partition Editor)

delete your 8.04 partition, resize the partitions as you wish.

you may want to take the 8.04 entry out of your grub menu too.

---

### Post by indiana_crook on 2008-04-28
originally wanted to, but that went sour.  I had Windows Vista before and wanted to dual boot with that, but I failed at that too.  But I will definatley do the install.  Can I change it without having to reinstall 7.10.

---

### Post by indiana_crook on 2008-04-28
> **Tatty said:**
> Boot into a live cd then load gparted (System->Administration->Partition Editor)

delete your 8.04 partition, resize the partitions as you wish.

you may want to take the 8.04 entry out of your grub menu too.

Okay, how do I take it out of the grub menu?

---

### Post by Tatty on 2008-04-28
In your 7.10 partition go to /boot/grub/menu.lst and find the entry for 8.04 and delete it.  Or if you are unsure you could just [reinstall grub]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

---

