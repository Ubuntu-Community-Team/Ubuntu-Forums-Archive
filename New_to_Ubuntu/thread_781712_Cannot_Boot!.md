---
title: "Cannot Boot!"
date: 2008-05-04
forum: New to Ubuntu
---

### Post by jeremycollins08 on 2008-05-04
I had Ubuntu 8.04 dual booted with WinXP. I needed to uninstall Ubuntu (only temporarily) and only have WindowsXP. I inserted the Ubuntu 7.10 live cd (that is the only version I have on cd) and ran Gparted. I removed all the ubuntu partitions and resized my windows partition. Now, when I load up my computer, I get this:

```
GRUB Loading stage 1.5.
GRUB loading, please wait...
Error 22
```

I cannot boot into WinXP, and the only way I could do anything is through the 7.10 live cd.

Does anyone know what to do? I need my computer to boot to WinXP, like it would normally before ever installing Ubuntu. 

Thanks, and your help will be greatly appreciated!

---

### Post by overdrank on 2008-05-04
> **jeremycollins08 said:**
> I had Ubuntu 8.04 dual booted with WinXP. I needed to uninstall Ubuntu (only temporarily) and only have WindowsXP. I inserted the Ubuntu 7.10 live cd (that is the only version I have on cd) and ran Gparted. I removed all the ubuntu partitions and resized my windows partition. Now, when I load up my computer, I get this:

```
GRUB Loading stage 1.5.
GRUB loading, please wait...
Error 22
```

I cannot boot into WinXP, and the only way I could do anything is through the 7.10 live cd.

Does anyone know what to do? I need my computer to boot to WinXP, like it would normally before ever installing Ubuntu. 

Thanks, and your help will be greatly appreciated!
HI and this link may help with the uninstall of ubuntu
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)
you will have to fix the mbr for windows.

---

### Post by 1234 on 2008-05-04
you may try to update the mbr of the disk with windows cd and get your xp back.
with the same case i just inserted my xp cd, boot the system with it and stopped it before installing and it just worked well.

---

### Post by zot171 on 2008-05-13
I have the same problem, but with Error 21 instead of Error 22, and I don't have the Windows CD (hand-me-down comp) any suggestions?

---

### Post by overdrank on 2008-05-13
> **zot171 said:**
> I have the same problem, but with Error 21 instead of Error 22, and I don't have the Windows CD (hand-me-down comp) any suggestions?

HI and maybe this 
[http://www.users.bigpond.net.au/hermanzone/p18.htm#Windows_98_Floppy_Disk_Method](http://www.users.bigpond.net.au/hermanzone/p18.htm#Windows_98_Floppy_Disk_Method)

---

### Post by Oldsoldier2003 on 2008-05-13
> **zot171 said:**
> I have the same problem, but with Error 21 instead of Error 22, and I don't have the Windows CD (hand-me-down comp) any suggestions?

download a supergrub live cd and use it to restore your windows mbr.

---

### Post by philinux on 2008-05-13
+1 supergrub is superb.

---

