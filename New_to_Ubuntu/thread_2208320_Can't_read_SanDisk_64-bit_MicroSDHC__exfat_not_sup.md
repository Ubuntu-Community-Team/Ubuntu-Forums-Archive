---
title: "Can't read SanDisk 64-bit MicroSDHC:  exfat not supported?"
date: 2014-02-27
forum: New to Ubuntu
---

### Post by jasonchr on 2014-02-27
Running Ubuntu 13.10 on System 76 Gazelle.

The SDHC is from a GoPro Hero 3 camera.

$ lspci
00:00.0 Host bridge: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor DRAM Controller (rev 06)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor PCI Express x16 Controller (rev 06)
00:02.0 VGA compatible controller: Intel Corporation 4th Gen Core Processor Integrated Graphics Controller (rev 06)
00:03.0 Audio device: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller (rev 06)
00:14.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB xHCI (rev 05)
00:16.0 Communication controller: Intel Corporation 8 Series/C220 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 8 Series/C220 Series Chipset High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #1 (rev d5)
00:1c.2 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #3 (rev d5)
00:1c.3 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #4 (rev d5)
00:1d.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation HM86 Express LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 8 Series/C220 Series Chipset Family 6-port SATA Controller 1 [AHCI mode] (rev 05)
00:1f.3 SMBus: Intel Corporation 8 Series/C220 Series Chipset Family SMBus Controller (rev 05)
03:00.0 Network controller: Intel Corporation Centrino Wireless-N 2230 (rev c4)
[COLOR=#ff0000]***04:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. Device 5289 (rev 01)***[/COLOR]
04:00.2 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 0a)

I am pretty sure the red line is my card.

When I insert the card (using an adapter into the onboard SD card reader I get:

[ATTACH=CONFIG]250738[/ATTACH]

(too small to read?  it says:  "Error mounting /dev/mmcblk0p1 at /media/jason/9C33-6BBD: Command-line `mount -t "exfat" -o "uhelper=udisks2,nodev,nosuid" "/dev/mmcblk0p1" "/media/jason/9C33-6BBD"' exited with non-zero exit status 32: mount: unknown filesystem type 'exfat'  ")

Just for fun I tryed mounting it manually (after creating a mount-point /media/jason/MicroSDHC using **mkdir /media/jason/MicroSDHC** ):


$ sudo mount -t "exfat" -o "uhelper=udisks2,nodev,nosuid" "/dev/mmcblk0p1" "/media/jason/MicroSDHC"
mount: unknown filesystem type 'exfat'

Is exfat supported in ubuntu 13.10?  

Any pointers to how to get this working?   ... it has been many years since I compiled a kernel and I think I may be too old to learn again, but I am willing  to try ...

--Jason

---

### Post by heyheyhey on 2014-07-31
Jason,

I've just unboxed my GoPro and am having the exact same problem. Did you figure it out yet as I could use the help?
I get the same message from both automount and when trying the manual mounting.

Cheers,

Josh

NB: just trawled through a few more threads and solved the problem, for me at least. 
sudo apt-get update
sudo apt-get install exfat-utils

Good luck

---

