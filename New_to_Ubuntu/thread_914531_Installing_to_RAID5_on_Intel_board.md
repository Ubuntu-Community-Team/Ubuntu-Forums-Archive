---
title: "Installing to RAID5 on Intel board"
date: 2008-09-08
forum: New to Ubuntu
---

### Post by User113 on 2008-09-08
I have installed Ubuntu (dual boot w/ Win XP) on one of my older computers, but the drive is failing and it often both XP and Linux crash or lock up.  So I built myself a new machine hoping to install dual boot on it using RAID5.  I have four 750GB SATA drives from WD ( [http://www.wdc.com/en/products/products.asp?driveid=335](http://www.wdc.com/en/products/products.asp?driveid=335) ) set up as two RAID5 volumes.  The mobo is the Intel DP35DP ( [http://support.intel.com/Products/Desktop/Motherboards/DP35DP/DP35DP-overview.htm](http://support.intel.com/Products/Desktop/Motherboards/DP35DP/DP35DP-overview.htm) ) with a Core 2 Quad Q6600 processor.  Everything on the mobo works fine in RAID 5 with Vista, but that is not the ultimate setup that I want on this machine.

I was hoping to format and partition the disks using GParted (like I did with the previous install) but I can't figure out how.  I don't have a clue as to which extra modules to load, and I can't set up the disks with Win-XP because the mobo does not even have a floppy header on it so that I can load the required drivers (Win XP requries that all drivers be loaded via floppy disks; I find this totally stupid because the mobo came with a floppy disk with drivers and the product guide was apparantly copied form a different board as it has references to installing drivers via the floppy disk, I do not have any idea as to what Intel was thinking).

I thought I would be clever and install Vista first (which I was able to do, since it has the ability to load drivers from a CD, which also came with the mobo) and then install XP and ubuntu, but that didn't work either.  Neither of them recognized the RAID5 volumes.  Does anybody have any suggestions, or is this mobo limited to RAID5 mode with Vista only?

P.S. The DP35DP is listed on the desktop hardware incompatibility list for the Gigabit Ethernet Controller and apparantly some other attached hardware which suggests that at least some disk configurations are viable with ubuntu...

---

