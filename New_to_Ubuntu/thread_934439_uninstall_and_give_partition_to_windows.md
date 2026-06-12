---
title: "uninstall and give partition to windows"
date: 2008-09-30
forum: New to Ubuntu
---

### Post by dd1313 on 2008-09-30
Hello Friends

I have windows xp pro and ubuntu 6 on my machine.
I want to uninstall ubuntu and resize  windows or maybe have
a seperate partition that windows can see.

Problem is that Windows cannot see ubuntu at the moment.

How can I do this please

THanks
Shaun

--

---

### Post by Harisz750 on 2008-09-30
use the live cd and resize with Gparted partition editor

---

### Post by PriceChild on 2008-09-30
Please see microsoft's support site for help restoring their boot loader: [http://support.microsoft.com/kb/314058/en-us](http://support.microsoft.com/kb/314058/en-us) (You want to use the 'fixmbr' line iirc)

I believe the best option for deleting the ubuntu partition and enlarging the windows one to fill the space would be to use the partitioner on the ubuntu live cd, but remember to backup all data first.

---

### Post by dd1313 on 2008-10-01
> **Harisz750 said:**
> use the live cd and resize with Gparted partition editor


How do I do this please

THanks
Shaun

---

### Post by Elfy on 2008-10-01
Use the link in pricechilds post to get the win bootloader installed before you remove the ubuntu partition.

Boot with the livecd - partition editor is in the system admin menu.

Right click the swap partition and turn it off.

Right click the partitions you wish to remove and select delete - apply.

Resize the win partition.

Ensure you have suitable backups

---

