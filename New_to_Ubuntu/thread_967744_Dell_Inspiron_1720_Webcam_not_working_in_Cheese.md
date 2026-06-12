---
title: "Dell Inspiron 1720 Webcam not working in Cheese"
date: 2008-11-02
forum: New to Ubuntu
---

### Post by tompickles on 2008-11-02
Hello, I cannot get my webcam to work. lspci yeilds no results as far as I can see about webcams:

```
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
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
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8600M GT (rev a1)
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
03:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
0c:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)

```

Any thoughts?

Running from Terminal produces no errors, however, there is just a blank box where I should be! Also, when I hit the X, it asks me whether I want to Force Quit or Cancel. Terminal here says "Killed."

---

### Post by tompickles on 2008-11-02
Bump!

---

### Post by tompickles on 2008-11-09
Bump- would love your thoughts on this guys. My webcam worked in 8.04.

---

### Post by tompickles on 2008-11-09
Cheese now says no Webcam Found

---

### Post by tompickles on 2008-11-09
dmesg | grep cam yields this:

[   14.576097] uvcvideo: Found UVC 1.00 device Laptop Integrated Webcam (05a9:2640)

How do I force gstreamer to use this?

---

### Post by tompickles on 2008-11-09
Mods - can you please move this into the Hardware section - perhaps it will get a better viewing there?

---

### Post by DigitEyez on 2008-12-08
I have the same problem. On 8.04 Cheese worked.
Once I updated to 8.10 when cheese starts the webcam light comes on.
It does not complain about not finding the webcam but it just leaves window white.

I don't think the picture is actually taken, because it is not shown as a thumbnail afterwards.

terminal output from cheese:
```
(cheese:14460): GStreamer-WARNING **: pad source:src returned caps which are not a real subset of its template caps

(cheese:14460): GStreamer-WARNING **: pad source:src returned caps which are not a real subset of its template caps

(cheese:14460): GStreamer-WARNING **: pad video_source:src returned caps which are not a real subset of its template caps
```

My webcam works just fine in other applications though... I tried it in Ekiga, VLC & Skype

So for me at least its not a hardware problem.

---

### Post by nhasian on 2008-12-10
I found this:

[http://bugzilla.gnome.org/show_bug.cgi?id=545033](http://bugzilla.gnome.org/show_bug.cgi?id=545033)

---

### Post by Mizai on 2009-01-06
So has this patch not been applied yet? My Inspiron 1720 webcam still doesn't work in any program other than Ekiga.

---

