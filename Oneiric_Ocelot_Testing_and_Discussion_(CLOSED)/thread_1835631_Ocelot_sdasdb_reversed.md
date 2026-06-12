---
title: "Ocelot sda/sdb reversed"
date: 2011-08-29
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by jerrylamos on 2011-08-29
Here's my two drive setup.  Ocelot is reversed on sda/sdb
```

Drive_type     IDE      SATA
Bios           boot
Lynx           sda      sdb
Meerkat        sda      sdb
Narwhal        sda      sdb
Ocelot         sdb      sda

```
Found that out a few weeks ago so I cope with it.  Just one of those anklebiters.

Even the Grub2 boot menus switch sdb for sda on Ocelot - this is a 5 boot system spread across the two hard drives.

Both the Ocelot Live and installed images do the same thing.

Let the buyer beware.

Jerry

---

### Post by fjgaude on 2011-08-29
Strange, but thanks for the alert, Jerry! It doesn't do such a thing on my three-drive system. Oneiric stays as /dev/sda2 and Natty stays as /dev/sda1... Maverick stays as /dev/sdb1...

All x64 on my main box. On my netbook, x32, there's no switch on the dual boot.

---

### Post by MacUntu on 2011-08-29
Well, that's why we use UUIDs - you should never rely on those /dev/sdX names.

---

### Post by jerrylamos on 2011-08-29
> **MacUntu said:**
> Well, that's why we use UUIDs - you should never rely on those /dev/sdX names.

UUID's don't help here.  Grub looks on the wrong sdx for the UUID and it never occurs to Grub to look on the other sdx where that UUID actually is.

Jerry

---

### Post by fjgaude on 2011-08-29
Say, try doing these when on the boot of /dev/sda1:

```
sudo update-grub
sudo grub-install /dev/sda
```

That likely will fix your issue.

---

### Post by jerrylamos on 2011-08-30
> **fjgaude said:**
> Say, try doing these when on the boot of /dev/sda1:

```
sudo update-grub
sudo grub-install /dev/sda
```

That likely will fix your issue.

If I do what you recommend which is the usual procedure, on Narwhal it updates the boot IDE drive and I can boot wherein it says Narwhal is on /dev/sda which boots fine.  It says Oneiric is on /dev/sda8. If I select /dev/sda8 up comes Oneiric which insists it is on /dev/sdb, not what Grub said. 

Now Oneiric is physically on the same IDE drive.  If I do what you recommend, normal procedure, Oneiric busily updates the SATA drive which is not the boot drive.  

So when I boot, I still get Narwhal since boot is set to the IDE drive.

Oneiric updated the SATA which isn't the boot drive so I don't get the Oneiric /boot/grub/grub.cfg.

Now I could try on Oneiric sudo grub-install /dev/sdb but I don't bother, since gosh knows what it will do to the Lynx, Meerkat, and Narwhal boot selections.

Thanks, Jerry

---

