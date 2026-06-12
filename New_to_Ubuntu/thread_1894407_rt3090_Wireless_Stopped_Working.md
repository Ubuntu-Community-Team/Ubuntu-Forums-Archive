---
title: "rt3090 Wireless Stopped Working"
date: 2011-12-12
forum: New to Ubuntu
---

### Post by mps69 on 2011-12-12
I'm a bit at my wits end with this one.
Running 11.10 on my netbook, it was all going fine until one of the latest updates wiped out my wireless link.
No idea why this keeps happening with some updates, it's a bit frustrating to say the least.
I've tried looking around the forums without any great success, so could someone please point me in the right direction.
lshw network output is
> *-network UNCLAIMED     
       description: Network controller
       product: RT3090 Wireless 802.11n 1T/1R PCIe
       vendor: Ralink corp.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:f0100000-f010ffff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 02
       serial: 00:03:0d:d5:0c:b0
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=N/A ip=192.168.0.8 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:43 ioport:2000(size=256) memory:f0510000-f0510fff memory:f0500000-f050ffff memory:f0520000-f053ffff

lspci output is
> 03:00.0 Network controller: Ralink corp. RT3090 Wireless 802.11n 1T/1R PCIe
Blacklist output is
> # This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac

I've also installed the latest drives for the rt3090, well I think they are the latest ones.
Any more information needed let me know.
Cheers

---

### Post by gandaran on 2011-12-12
if you compiled the drivers you will have to do it again every time there is a kernel update.

---

### Post by anewguy on 2011-12-12
+1.  And if you watched your update, you probably saw the new kernel being delivered. While not as frequent as other updates, kernel updates will occur as part of the normal system update process.  When this happens, any module, such as a device driver, that was compiled and relied upon the old kernels header files, etc., needs to be recompiled.

In the case of wireless networking, this is the main reason we push for using a native driver if at all possible.  Any other drivers not directly supported by ubuntu will in all likelyhood need recompilation at each kernel change.

Dave ;)

---

