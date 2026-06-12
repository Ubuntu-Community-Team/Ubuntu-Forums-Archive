---
title: "Ubuntu does not detect onboard DVI connected monitor after installing AMD Catalyst"
date: 2015-04-14
forum: New to Ubuntu
---

### Post by LordNinjaMelon on 2015-04-14
I was running fresh ubuntu installation with 3 monitors, 2 of them are connected to a single Radeon HD6950 and the third is connected to on-board DVI slot. It was working completely out-of-the-box except the issue with [mouse flickering]("http://ubuntuforums.org/showthread.php?t=2273536")
The poster asked what are my driver version, so then I realized I should install Linux version of Radeon HD6950 driver even though I already did that on Windows. After the installation of the current AMD Catalyst suite Ubuntu no longer recognizes the third monitor. 

I have already restarting multiple times and checking Display app, but I am unable to find the third monitor

---

### Post by QIII on 2015-04-14
Hello!

What is the OEM and model of the on-board adapter?

---

### Post by LordNinjaMelon on 2015-04-14
> **QIII said:**
> Hello!

What is the OEM and model of the on-board adapter?

I am unable to find any information about that in the motherboard's manual. I am using GA-Z68AP-D3, is there a way to find the OEM and the model through software?

---

### Post by Vladlenin5000 on 2015-04-14
[Gigabyte GA-Z68AP-D3]("http://www.gigabyte.com/products/product-page.aspx?pid=4015#sp")

---

### Post by cariboo on 2015-04-14
> **LordNinjaMelon said:**
> I am unable to find any information about that in the motherboard's manual. I am using GA-Z68AP-D3, is there a way to find the OEM and the model through software?

You can find all sorts of info about your hardware by using lshw:

```
sudo lshw
```

will list everything, to find what video hardware your system uses:

```
sudo lshw -C disply
```

the above command results in this, on the system I'm using at the moment:

```
sudo lshw -C display
[sudo] password for cariboo: 
  *-display               
       description: VGA compatible controller
       product: Atom Processor Z36xxx/Z37xxx Series Graphics & Display
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 0e
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:92 memory:d0000000-d03fffff memory:c0000000-cfffffff ioport:f080(size=8)
```

---

### Post by LordNinjaMelon on 2015-04-16
> **Vladlenin5000 said:**
> [Gigabyte GA-Z68AP-D3]("http://www.gigabyte.com/products/product-page.aspx?pid=4015#sp")
Yeah, that's the one. But I can't find the manufacturer for the HDMI connection

> **cariboo907 said:**
> You can find all sorts of info about your hardware by using lshw


Oh, that's a cool feature! Here's my output:
```

PCI (sysfs) 
  *-display               
       description: VGA compatible controller
       product: Cayman PRO [Radeon HD 6950]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=fglrx_pci latency=0
       resources: irq:52 memory:c0000000-cfffffff memory:fe620000-fe63ffff ioport:e000(size=256) memory:fe600000-fe61ffff
  *-display
       description: Display controller
       product: 2nd Generation Core Processor Family Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm bus_master cap_list
       configuration: driver=i915 latency=0
       resources: irq:51 memory:fe000000-fe3fffff memory:b0000000-bfffffff ioport:f000(size=64)

```

---

### Post by mastablasta on 2015-04-16
the other one is Intel. you likely need to initialise the chip after AMD drivers install. see here for more info: [https://help.ubuntu.com/community/BinaryDriverHowto/AMD](https://help.ubuntu.com/community/BinaryDriverHowto/AMD)


hopefully proprietary driver will resolve your flickering. still it might be good to give some feedback about this issue to AMD opensource drivers team (e.g. bug report...).

---

### Post by LordNinjaMelon on 2015-04-29
> **mastablasta said:**
> the other one is Intel. you likely need to initialise the chip after AMD drivers install. see here for more info: [https://help.ubuntu.com/community/BinaryDriverHowto/AMD](https://help.ubuntu.com/community/BinaryDriverHowto/AMD)


hopefully proprietary driver will resolve your flickering. still it might be good to give some feedback about this issue to AMD opensource drivers team (e.g. bug report...).

Sorry for the slow reply, it's a busy exam month

I assume you mean the "3.2. Manually installing Catalyst 13.4, special case for Intel/AMD hybrid graphics", right? The way I understand is that it will let me change between using AMD GPU and Intel integrated graphics card whenever I reboot, but my goal is to make it work simultaneous. 
It was working fine before I installed the AMD drivers, except the mouse flickering.

---

### Post by sandyd on 2015-04-29
> **mastablasta said:**
> the other one is Intel. you likely need to initialise the chip after AMD drivers install. see here for more info: [https://help.ubuntu.com/community/BinaryDriverHowto/AMD](https://help.ubuntu.com/community/BinaryDriverHowto/AMD)


hopefully proprietary driver will resolve your flickering. still it might be good to give some feedback about this issue to AMD opensource drivers team (e.g. bug report...).

Already a bug report -> [https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/1278223](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/1278223)

---

### Post by LordNinjaMelon on 2015-05-05
> **sandyd said:**
> Already a bug report -> [https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/1278223](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/1278223)

Yeah, that was my original problem. I installed AMD drivers to try to solve it and now it doesn't even detect the 3rd monitor

---

