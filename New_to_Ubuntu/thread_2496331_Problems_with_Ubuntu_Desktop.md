---
title: "Problems with Ubuntu Desktop"
date: 2024-03-24
forum: New to Ubuntu
---

### Post by devnullman2 on 2024-03-24
I created a bootable USB from ubuntu-22.04.4-desktop-amd64.iso, booted it, got to the screen to choose between 'Try' and 'Install'. I chose 'Try' and this is what I got:

2.745624 SCSI 5:0:0:1 Wrong diagnostic page, asked for 1 got 8
2.745629 SCSI 5:0:0:1 Failed to get diagnostic page 1
2.745631 SCSI 5:0:0:1 Failed to bind enclosure -19

That is all I got, I left it alone for 30 minutes, then tried CRTL-C, CTRL-ALT-DEL a few times and gave up.

The Computer is a very new DELL XPS8950, I-7 Gen 12, 32 GB RAM, NVIDIA GeForce RTX 3060 Video

Help please. . . .

---

### Post by TheFu on 2024-03-24
nvidia commonly has issues with Ubuntu due to their licenses for drivers.  I'd start by looking for nvidia specific boot options.
[https://forums.developer.nvidia.com/t/issues-booting-up-ubuntu-os-with-nvidia-geforce-rtx-3060/241651](https://forums.developer.nvidia.com/t/issues-booting-up-ubuntu-os-with-nvidia-geforce-rtx-3060/241651)
[https://askubuntu.com/questions/1449051/ubuntu-22-04-not-booting-after-i-installed-nvidia-drivers](https://askubuntu.com/questions/1449051/ubuntu-22-04-not-booting-after-i-installed-nvidia-drivers)

Are some ideas.

---

### Post by devnullman2 on 2024-03-27
Why would NVIDIA driver problems show up as SCSI 5:0:0:1 ?

---

### Post by oldfred on 2024-03-27
Do you have latest UEFI firmware from Dell?
And latest firmware for any NVMe or SATA SSD drives?

How many drives do you have installed?
If you have a NVMe drive, it may conflict with one of the SATA ports. Check your manual.

---

### Post by devnullman2 on 2024-04-03
Yes all DELL updates are current
2 internal HDD's, one NVMe drive, all firmware current, BIOS just updated last week
Windows 11 no problems, Linux Mint no problems

---

