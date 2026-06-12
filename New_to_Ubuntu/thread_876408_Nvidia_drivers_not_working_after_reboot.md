---
title: "Nvidia drivers not working after reboot"
date: 2008-07-31
forum: New to Ubuntu
---

### Post by brback on 2008-07-31
I downloaded the latest drivers from nVidia and managed to install them and everything looked great. But after a reboot my resolution turned down to minimum, and something is apparently wrong. I've tried to read around the web to figure out this, but haven't found anything that have helped me yet.

I am still very new to Linux so any help is much appreciated.

---

### Post by tuxxy on 2008-07-31
Did you enable them from system > admin > hardware drivers?

---

### Post by Neo0351 on 2008-07-31
do the last part of this tread
[http://ubuntuforums.org/showpost.php?p=4558708&postcount=37](http://ubuntuforums.org/showpost.php?p=4558708&postcount=37)

---

### Post by brback on 2008-07-31
wow, thanks for fast answer!

I've done the first part, but i am unsure where /location/to/driver is located?

---

### Post by brback on 2008-07-31
Okay, I think i managed to do all mentioned in thread posted, but it still hasn't gotten me anywhere

By enabling system > admin > hardware drivers wont that enable the drivers that come with the ubuntu installation?

---

### Post by Neo0351 on 2008-07-31
post ```
lspci
```

---

### Post by brback on 2008-07-31
lspci says:

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation GeForce Go 7900 GTX (rev a1)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
03:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 0a)
03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 05)
03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
09:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5752 Gigabit Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)

---

### Post by Neo0351 on 2008-07-31
you should be able to enable your drivers through system > admin > hardware drivers
make sure to edit your 
```
nano /etc/default/linux-restricted-modules-common
```
to look like this
```
DISABLED_MODULES=""
```
if that doesnt work, try envy
[http://albertomilone.com/envyngfaq.html#A](http://albertomilone.com/envyngfaq.html#A)

---

### Post by brback on 2008-07-31
changed back to DISABLED_MODULES="" though your linked thread said otherwise.

Would an API mismatch have any impact on this subject?
because it says so after trying startx that i got it, and it ask of me to get the same version of the driver and kernel module or something whatever that means.

---

### Post by tuxxy on 2008-07-31
Search for envy in synaptic, you could try and install through this.

---

### Post by brback on 2008-07-31
Envy made everything work as it should so far!

Thanks alot!

---

