---
title: "Ubuntu 17.10 doesn't install on NUC7i7 w/ M.2 NVMe 960"
date: 2017-12-03
forum: New to Ubuntu
---

### Post by ckotan on 2017-12-03
I've been working at this a couple of days. I created a USB with Ubuntu 17.10 and booted it as EUFI device.  I connected to a wifi, ran GPartED and deleted partition table from nvme0n1.  Started install. I selected option to have Ubuntu install an EFI partition and an ext partition.

Intel Visual Bios has EUFI enabled, Legacy disabled.

Install finished with error that it cannot install packages from /cdrom, same as always. GParted shows nvme0n1 with about 1MB in the EFI part and 1GB in the ext4 partition.

Reboot - nothing.  Bios shows only LAN options to boot from in EUFI.  The Samsung M.2 960 shows in PCI, but I see no way to make it appear in the EUFI boot devices.

I could sure use some help.  TIA.

---

### Post by Geoffrey_Arndt on 2017-12-04
1 Gig for the whole OS (ext4)?  . . . .  what else is on the ssd?   Is this an Ubuntu only system?    Need a minimum of 8 gig or so, but a _40 to 60 Gig ext4 partition _is much better for stability and expansion.

---

### Post by ckotan on 2017-12-04
The parition sizes are 500MB for the boot, 200+GB for the Ext4. GParted shows 1.02MB data in the boot, 1 GB in the ext4. This will be a Linux only system - I'll put Windows in a VM if necessary.  TNX!

---

### Post by Geoffrey_Arndt on 2017-12-05
Linux requires a Linux file-system to intstall the OS to.    If ONLY 1GB is formatted ext4, out of 200+GB in the partition - - then what is the 199 GB formatted as?   Is it "unallocated" space?   Perhaps a screen-pic from gparted will help clarify.

---

