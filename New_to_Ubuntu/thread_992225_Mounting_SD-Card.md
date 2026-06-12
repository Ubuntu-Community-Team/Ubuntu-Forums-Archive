---
title: "Mounting SD-Card"
date: 2008-11-24
forum: New to Ubuntu
---

### Post by shoot2kill on 2008-11-24
i have an SD card reader in my computer which windows can use fine, so i know it is working ok. but in ubuntu it just does nothing, no mount error window or anything.. is there a way i can manually mount it, and how do i find out what /dev/xxx path it is ??

---

### Post by bobnutfield on 2008-11-24
The card reader in my computer shows up in lspci as the last entry.  When I insert it, it hotplugs in the same way that USB stick does.  Have you ran lspci to see if it is being recognized?  If it is, then run:

> sudo fdisk -l

It should show up as /dev/sdb.  If it does not show up in the fdisk command, you missing the driver.  Type:

> sudo lsmod

and look for sdhci_pci.  That is the module that controls the SD card reader.  If it is not there, try to modprobe it.

---

### Post by shoot2kill on 2008-11-24
i can use a USb pen fine,and it auto mounts, but this doesnt.. 

my fdisk -l : not listed
```

Disk /dev/sda: 74.3 GB, 74355769344 bytes
255 heads, 63 sectors/track, 9039 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc46bc46b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9040    72610816    7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc4e8c4e8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001    7  HPFS/NTFS

Disk /dev/sdc: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x60c84ab9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       91202   732571648    7  HPFS/NTFS

Disk /dev/sdd: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xda2d0d48

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1       10011    80413326    7  HPFS/NTFS

```

lspci:
```

00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation 82801IR (ICH9R) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801IR/IO/IH (ICH9R/DO/DH) 4 port SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801I (ICH9 Family) 2 port SATA IDE Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc RV570 [Radeon X1950 Pro] (rev 9a)
01:00.1 Display controller: ATI Technologies Inc RV570 [Radeon X1950 Pro] (secondary) (rev 9a)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8056 PCI-E Gigabit Ethernet Controller (rev 12)
03:00.0 SATA controller: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 03)
03:00.1 IDE interface: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 03)


```

---

### Post by bobnutfield on 2008-11-24
Hmmmm....you are right. It does not seem to be recognized by the system.  The lspci output should have shown something like:

> 14:06.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)

as it does on my laptop.  Of course your manufacturer may be different, but I think the driver is the same.  You might go do the the "Device" section in Windows and get the full identification of the interface.  Then, it can be googled to determine how to get it recognized and working.

---

