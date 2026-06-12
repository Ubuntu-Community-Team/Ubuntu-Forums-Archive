---
title: "Ubuntu doesn't always complete shutdown process"
date: 2018-08-22
forum: New to Ubuntu
---

### Post by richpri on 2018-08-22
I have shut down my new Ubuntu 18.04 release about 6 times now. All but once it has hung with power still on. The screen has the following message: "reboot: Powerdown". From reading other posts I get that this is a hard to diagnose problem. There seems to be some controversy about the GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi=off" workaround. Thus I hesitate to use it.

Following the recommendation from DuckHook I am including the following hardware information:

```
sudo lshw -C display,network,multimedia,power && df -h && sudo blkid && cat fstab 
       description: VGA compatible controller
       product: GK208 [GeForce GT 710B]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:27 memory:fd000000-fdffffff memory:f0000000-f7ffffff memory:f8000000-f9ffffff ioport:e000(size=128) memory:c0000-dffff
  *-multimedia
       description: Audio device
       product: GK208 HDMI/DP Audio Controller
       vendor: NVIDIA Corporation
       physical id: 0.1
       bus info: pci@0000:01:00.1
       version: a1
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=snd_hda_intel latency=0
       resources: irq:19 memory:fe080000-fe083fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: enp2s0
       version: 06
       serial: 74:d4:35:a1:33:70
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8168e-3_0.0.4 03/27/12 ip=192.168.0.103 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:16 ioport:d000(size=256) memory:fe100000-fe100fff memory:fa100000-fa103fff
  *-usb
       description: Audio device
       product: INSIGNIA USB MIC Device
       vendor: INSIGNIA
       physical id: 5
       bus info: usb@5:5
       version: 1.00
       serial: 14000001
       capabilities: usb-2.00 audio-control
       configuration: driver=usbhid maxpower=100mA speed=12Mbit/s
  *-multimedia
       description: Audio device
       product: FCH Azalia Controller
       vendor: Advanced Micro Devices, Inc. [AMD]
       physical id: 14.2
       bus info: pci@0000:00:14.2
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=snd_hda_intel latency=32
       resources: irq:16 memory:fe200000-fe203fff
Filesystem      Size  Used Avail Use% Mounted on
udev            3.9G     0  3.9G   0% /dev
tmpfs           793M  1.9M  791M   1% /run
/dev/sda1       452G   21G  408G   5% /
tmpfs           3.9G   21M  3.9G   1% /dev/shm
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
tmpfs           3.9G     0  3.9G   0% /sys/fs/cgroup
/dev/loop0       15M   15M     0 100% /snap/gnome-logs/37
/dev/loop1      2.4M  2.4M     0 100% /snap/gnome-calculator/180
/dev/loop2      3.8M  3.8M     0 100% /snap/gnome-system-monitor/51
/dev/loop3       35M   35M     0 100% /snap/gtk-common-themes/319
/dev/loop4       87M   87M     0 100% /snap/core/5145
/dev/loop6       13M   13M     0 100% /snap/gnome-characters/103
/dev/loop7      141M  141M     0 100% /snap/gnome-3-26-1604/70
/dev/loop5      5.0M  5.0M     0 100% /snap/canonical-livepatch/42
tmpfs           792M   16K  792M   1% /run/user/125
tmpfs           792M   44K  792M   1% /run/user/1000
/dev/sdb1        30G  8.8G   21G  31% /media/rich/RedFlashDri
/dev/loop0: TYPE="squashfs"
/dev/loop1: TYPE="squashfs"
/dev/loop2: TYPE="squashfs"
/dev/loop3: TYPE="squashfs"
/dev/loop4: TYPE="squashfs"
/dev/loop5: TYPE="squashfs"
/dev/loop6: TYPE="squashfs"
/dev/loop7: TYPE="squashfs"
/dev/sda1: UUID="cf42d751-b915-4f6e-8c68-68d41664cefe" TYPE="ext4" PARTUUID="934a4e90-01"
/dev/sda5: UUID="4cfbc3eb-f25f-4b72-b82f-9deeade793d2" TYPE="swap" PARTUUID="934a4e90-05"
/dev/sdb1: LABEL="RedFlashDri" UUID="66DB-2582" TYPE="vfat"
cat: fstab: No such file or directory
```

Please let me know if I need to supply any other information.

---

### Post by TheFu on 2018-08-22
Does **sudo shutdown now -h** work or is this just a GUI problem?

---

### Post by richpri on 2018-08-22
Tried **sudo shutdown now -h** and it still hung. But it hung showing the ubuntu splash screen.

---

### Post by TheFu on 2018-08-22
Posting the same issue in multiple places, not good.

---

### Post by richpri on 2018-08-22
It was a mistake, sorry. I thought I was posting to my thread. When I found my mistake I could not figure out how to erase the first post.

---

### Post by QIII on 2018-08-22
Hello!

There is no way for you to "erase" a post.  Only the Staff can remove them from public view.

If you have made a post in error, please use the "Report Post" button to bring it to the attention of the Staff and ask for it to be removed.

Cheers!

---

