---
title: "Notebook HP Pavilion - 17-g050nl (ENERGY STAR) what video driver should I use?"
date: 2020-10-26
forum: New to Ubuntu
---

### Post by Netrunner on 2020-10-26
After issuing do-release-upgrade the Notebook HP Pavilion - 17-g050nl (ENERGY STAR) shows the verbose boot but does not show the login screen. 
The only way I have to get into the system is to: power down, power up, hit esc to get to the hp boot menu, hit enter to continue, hit esc to enter into the grub boot menu, select ubuntu recovery mode, open a root shell, edit the grub default and remove quiet spash or whatsoever and replace it with nomodeset, save , perform update grub, reboot. I guess Ubuntu 20.04.1 LTS does not recognize the video card or video driver that should be used with this hardware. What Drivers should I use to stop using nomodeset? How can I fix it?
If I boot normally, without nomodeset, all I get is a black screen. I had same problem 7 Years ago and fixed it somehow, but the do-release-upgrade must have erased my fix.
Kindest Regards

---

### Post by ActionParsnip on 2020-10-26
What is the output of:
```

sudo lshw -C display 

```

---

### Post by Netrunner on 2020-10-26
```
*-display UNCLAIMED       
       description: VGA compatible controller
       product: Wani [Radeon R5/R6/R7 Graphics]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 1
       bus info: pci@0000:00:01.0
       version: c5
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list
       configuration: latency=0
       resources: memory:d0000000-dfffffff memory:f0800000-f0ffffff ioport:f000(size=256) memory:feb00000-feb3ffff memory:c0000-dffff
  *-display UNCLAIMED
       description: Display controller
       product: Topaz XT [Radeon R7 M260/M265 / M340/M360 / M440/M445 / 530/535 / 620/625 Mobile]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 81
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi cap_list
       configuration: latency=0
       resources: memory:e0000000-efffffff memory:f0000000-f01fffff ioport:d000(size=256) memory:fe700000-fe73ffff memory:fe740000-fe75ffff
```

I even tried this
```

sudo add-apt-repository ppa:oibaf/graphics-drivers
sudo apt update && sudo apt -y upgrade 
```
following this guide: [https://linuxconfig.org/amd-radeon-ubuntu-20-04-driver-installation](https://linuxconfig.org/amd-radeon-ubuntu-20-04-driver-installation)
but I ended up with the usual black screen and then had to use "nomodeset". 
I don't understand why after the update of ubuntu release, the only way to have the video in my laptop is using the grub parameter GRUB_CMDLINE_LINUX_DEFAULT="nomodeset"

---

