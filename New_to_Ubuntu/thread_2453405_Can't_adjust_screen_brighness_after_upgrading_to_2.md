---
title: "Can't adjust screen brighness after upgrading to 20.10"
date: 2020-11-09
forum: New to Ubuntu
---

### Post by chinchillout on 2020-11-09
Hi there, I just upgraded from Ubuntu 20.04.1 LTS to 20.10 and  I can't adjust screen brightness anymore. The keyboard buttons for brightness don't work and the brightness slider is not visible in the tray or in Settings.

Showing no entries returned for:
```
 ls /sys/class/backlight
```

No effect after modifying my /etc/default/grub file to read
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_backlight=vendor"
```

I'm on the system-recommended Nvidia driver: 390.138 

```

lshw -c display
description: VGA compatible controller
       product: GK107M [GeForce GT 755M Mac Edition]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:67 memory:b0000000-b0ffffff memory:90000000-9fffffff memory:a0000000-a1ffffff ioport:1000(size=128) memory:b1000000-b107ffff
```

```
 
ubuntu-drivers devices
== /sys/devices/pci0000:00/0000:00:01.0/0000:01:00.0 ==
modalias : pci:v000010DEd00000FEAsv0000106Bsd0000011Fbc03sc00i00
vendor   : NVIDIA Corporation
model    : GK107M [GeForce GT 755M Mac Edition]
driver   : nvidia-driver-418-server - distro non-free
driver   : nvidia-driver-390 - distro non-free recommended
driver   : nvidia-340 - distro non-free
driver   : xserver-xorg-video-nouveau - distro free builtin

```


Thanks so much in advance for any help out!

---

### Post by ActionParsnip on 2020-11-10
Does the system have a make and model?
Do you have the latest BIOS?

---

### Post by pantazi on 2020-11-10
It was noted elsewhere that a fresh install rather than an upgrade may cure this problem.

My problem was solved with this:



[https://askubuntu.com/questions/7731...een-brightness]("https://askubuntu.com/questions/773155/artificially-increase-maximum-screen-brightness")

---

### Post by chinchillout on 2020-11-10
> It was noted elsewhere that a fresh install rather than an upgrade may cure this problem. My problem was solved with this: [https://askubuntu.com/questions/7731...een-brightness]("https://askubuntu.com/questions/773155/artificially-increase-maximum-screen-brightness")
Thanks! I was able to artificially tweak the brightness in terminal using that method. May need to do a fresh install if we can't find a solution here.

> Does the system have a make and model? Do you have the latest BIOS?

It's an Apple Late 2013 iMac 27". Yes the BIOS/EFI is up to date, since I am dual-booting OS X and have applied all OS X updates (including Catalina).

---

