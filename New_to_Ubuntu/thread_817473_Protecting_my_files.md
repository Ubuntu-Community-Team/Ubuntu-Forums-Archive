---
title: "Protecting my files"
date: 2008-06-03
forum: New to Ubuntu
---

### Post by MrPickle on 2008-06-03
Currently my graphics driver is disabled, obviously this makes me sad :P

I want to enable it, but last time I done this and restarted it would only display lots of random lines thus rendering it completely useless forcing me to re-format. Seems simple enough you say? Well no, because I had previously spent 8 hours getting my wireless card to work (Don't laugh :( ), Now I've lost the files I needed to make the wireless card work so I am reluctant to enable the card.

So, to get to the point, how can I safely enable the driver? Without having to reformat if it all goes pants?

---

### Post by spiderbatdad on 2008-06-03
MrPickle, please post the output of the command: ```
lspci
```so we know what hardware you have.

Also could you upload dmesg as an archive:```
dmesg > dmesg.txt
```will write a small file in your home directory. Right click that file and select 'create an archive' Use the manage attachment tool below to upload that archive here.

---

### Post by MrPickle on 2008-06-03
Will do.

> 00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8400M GS (rev a1)
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
03:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
0c:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)


The other thing was to big so I uploaded it here: [http://pastebin.com/f5333fad9](http://pastebin.com/f5333fad9)

---

### Post by spiderbatdad on 2008-06-03
I believe the driver you want may be here:[http://www.nvidia.com/object/linux_display_amd64_173.14.05.html](http://www.nvidia.com/object/linux_display_amd64_173.14.05.html)

See the instructions at bottom of page.

---

### Post by MrPickle on 2008-06-04
It's telling me I am running an X server and I need to exit the X server.

What is the X server? How do I close it?

---

### Post by MrPickle on 2008-06-04
Ok, I know how to exit the x server "sudo /etc/init.d/gdm stop" but it asks me to install the nvidia kernel, but when it tries to do that it fails to do so and exits the install.

---

