---
title: "[SOLVED] Installed on separate hd"
date: 2008-09-21
forum: New to Ubuntu
---

### Post by Elephantman5 on 2008-09-21
Started with xp. Restart, install ubuntu on separate hd. 
Grub never comes up, hd with xp is default. Xp boots up.

How do I change this?

---

### Post by jgedutis on 2008-09-24
Did you follow a guide for a dual boot installation or just install it onto another physical disk?  

If you installed on another disk the disk your bios is set to boot to is only booting to windows xp.  If you went into your bios  and set it to boot to the disk you installed ubuntu on, I bet it would start ubuntu but not windows.  

If the above is the case you could try to install grub on the Windows XP disk to give the option for XP or Ubuntu.  I would use the Super Grub boot disk for that.  Link is below.

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

### Post by Elephantman5 on 2008-09-24
I appreciate the link. I'll look into that.

---

### Post by caljohnsmith on 2008-09-24
I think it would be more ideal to keep Grub off your Windows XP drive, that way if anything happens to your Ubuntu drive, you will still be able to boot your Win XP drive. Personally I think the best solution in your situation is to make sure Grub is installed to the MBR (master boot record) of your Ubuntu drive, and then always boot from that drive; then you can simply add an entry in Grub's menu to boot your Windows XP. Is this something you might want to do? If so I can give specific instructions.

---

### Post by Elephantman5 on 2008-09-24
> **caljohnsmith said:**
> I think it would be more ideal to keep Grub off your Windows XP drive, that way if anything happens to your Ubuntu drive, you will still be able to boot your Win XP drive. Personally I think the best solution in your situation is to make sure Grub is installed to the MBR (master boot record) of your Ubuntu drive, and then always boot from that drive; then you can simply add an entry in Grub's menu to boot your Windows XP. Is this something you might want to do? If so I can give specific instructions.

This situation is long gone.
I will note your advice. I suppose I should have assigned the BIOS to boot from the Grubbed Ubuntu partition. (That is what you meant right?)

I suppose I would have used qgrub editor and added windows from there.

---

