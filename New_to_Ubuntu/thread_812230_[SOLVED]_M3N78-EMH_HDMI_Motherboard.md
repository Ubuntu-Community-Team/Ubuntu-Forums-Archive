---
title: "[SOLVED] M3N78-EMH HDMI Motherboard"
date: 2008-05-29
forum: New to Ubuntu
---

### Post by mike23 on 2008-05-29
Hi all..
I searched a lot about my problem but i only got more confused.. :(
Yesterday i upgraded to a M3N78-EMH HDMI Motherboard.. Only to find out that i cant install ubuntu coz it cant "see" my hard disk...
If anyone could help would be saving me.. 
Thanx

---

### Post by mike23 on 2008-05-29
Anyone please???  :S

---

### Post by philinux on 2008-05-29
I assume you've burned the live cd as in iso image, set your bios to boot from cdrom first.

Then what are your system specs and what are the error messages.

---

### Post by mike23 on 2008-05-29
Of course:D 
I get to the part where u have to choose partitions etc, and there is no hdd  to choose.
Btw hardware is ok coz i was forced to put xp on this right now.. :(

its the M3N78-EMH HDMI Motherboard
and the hdd is SEAGATE BARRACUDA 7200.11 ST3500320AS 500GB SATA2
CORSAIR XMS2 DDR2 4GB (2X2GB) 800MHZ 
NEC DVDRW
thanx

---

### Post by lazyart on 2008-05-29
From [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/199573](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/199573)

> Solution:

After activating AHCI in the bios setting and booting from CD/DVD one need to press F6 to enter further boot parameter: pci=nomsi
Now the hdd and other sata devices are recognized correctly due the installation. Don't know if its really a bug..


---

### Post by Unix_Slayer on 2008-05-29
Could also be something with the mbr. I had a Seagate Barracuda that did the same thing. That's why I don't buy any other drives, but Western Dig's.


> **lazyart said:**
> From [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/199573](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/199573)

---

### Post by mike23 on 2008-05-29
sorry but i cant find any AHCI option in my mobo.. and when i hit f6 theres no pci=nomsi option either....

---

### Post by lazyart on 2008-05-29
Should be in your SATA controller type.  When you hit F6 you have to enter the option shown above.

---

### Post by mike23 on 2008-05-29
ok found AHCI but...
hitting f6 only got me: acpi=off, noapic, nolapic, edd=on, free software only..
no pci=nomsi anyware..

and with AHCI mode i cant boot into xp, and, i actually want to dual boot.

ok now please someone tell me what is wrong with this mobo i mean if it isnt supported just someone tell me so, so i can just get rid of it. please.

---

### Post by lazyart on 2008-05-30
Nothing is wrong with your motherboard.

If you change the SATA type after an OS is installed then the OS won't see your drives.  You would have to reinstall Windows.  This is normal.

Then, after you hit F6 and you see all of those options YOU HAVE TO TYPE IN pci=nomsi AT THE END OF THE LINE.

Then continue booting up.

---

### Post by mike23 on 2008-05-31
Thanx this worked!

---

### Post by openElements on 2008-06-22
I have the same board and can't seem to get the onboard LAN to work.  how did you get it to work?

---

### Post by Unix_Slayer on 2008-06-22
> **openElements said:**
> I have the same board and can't seem to get the onboard LAN to work.  how did you get it to work?


Is it turned on in your bios? Do you know the chip manufacturer?

---

### Post by openElements on 2008-06-23
> **Unix_Slayer said:**
> Is it turned on in your bios? Do you know the chip manufacturer?

onboard LAN is set to auto in the bios.  I updated the bios (0409) from the ASUS website and the NIC is still dead.

I think i will just get the ASUS M3N-HD HDMI instead.

---

### Post by save2 on 2013-04-21
this may help you:
[http://ubuntuforums.org/showthread.php?t=2136506&p=12612114](http://ubuntuforums.org/showthread.php?t=2136506&p=12612114)

---

### Post by oldos2er on 2013-04-21
Closed, please don't bump old threads.

---

