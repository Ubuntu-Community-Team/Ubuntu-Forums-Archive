---
title: "Can't find usb media"
date: 2008-08-12
forum: New to Ubuntu
---

### Post by jjblackfox on 2008-08-12
Hello, my brother recently installed ubuntu on his computer and everything works fine, except for any usb devices.

He tried plugging his psp in and setting it to usb mode, but it didn't work. The psp realized that it was connected via a usb cable, but it didn't show up on the computer. I then tried my flash drive in and it didn't recognize it either. 

I tried other various devices, but the computer doesn't show that any devices are connected. 

Any suggestions?

---

### Post by dacorr on 2008-08-12
connect the device then from terminal type

lsusb - (lists usb devices)

and post its result

then

sudo fdisk -l (Lists drives/paritions)

then post the results

Dac

---

### Post by Cypher on 2008-08-12
Have USB devices worked on that computer before? Was it running Windows before? Are the keyboard/mouse USB devices or are they PS2??

---

### Post by jjblackfox on 2008-08-12
> **dacorr said:**
> connect the device then from terminal type

lsusb - (lists usb devices)

and post its result

then

sudo fdisk -l (Lists drives/paritions)

then post the results

Dac

When I type lsusb, it goes to the next line with no text on that line.

---

### Post by jjblackfox on 2008-08-12
> **Cypher said:**
> Have USB devices worked on that computer before? Was it running Windows before? Are the keyboard/mouse USB devices or are they PS2??

Both the keyboard and mouse are ps2, and he did have a usb mouse in windows, but it was really laggy. For a while he has a usb mouse in ubuntu, but it was laggy as well so he switched over to a ps2.

---

### Post by dacorr on 2008-08-12
lspci

does it list the USB controller?

---

### Post by jjblackfox on 2008-08-12
> **dacorr said:**
> lspci

does it list the USB controller?

Yes:
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)

---

### Post by Cypher on 2008-08-12
What version of Ubuntu and Kernel is this? "uname -a" will get you the Kernel info. The fact the the mouse (a low speed device) was laggy means that there might be something a little wonky with the USB port or something. A flash drive (a high speed device) would need a more reliable system to operate.

If the mouse was behaving badly..that doesn't bode well for the flash drive..

---

### Post by jjblackfox on 2008-08-12
> **Cypher said:**
> What version of Ubuntu and Kernel is this? "uname -a" will get you the Kernel info. The fact the the mouse (a low speed device) was laggy means that there might be something a little wonky with the USB port or something. A flash drive (a high speed device) would need a more reliable system to operate.

If the mouse was behaving badly..that doesn't bode well for the flash drive..

Linux henrico 2.6.24-19-generic #1 SMP Fri Jul 11 23:41:49 UTC 2008 i686 GNU/Linux

---

### Post by jjblackfox on 2008-08-12
bump

---

### Post by Cypher on 2008-08-12
How old is this computer? Perhaps the hardware is flaky..

---

### Post by jjblackfox on 2008-08-12
> **dacorr said:**
> connect the device then from terminal type

lsusb - (lists usb devices)

and post its result

then

sudo fdisk -l (Lists drives/paritions)

then post the results

Dac

sudo fdisk -l gives the following output:

Disk /dev/sda: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x94559455

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       24036   193069138+  83  Linux
/dev/sda2           24037       24792     6072570    5  Extended
/dev/sda5           24037       24792     6072538+  82  Linux swap / Solaris

Disk /dev/sdb: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x02afe264

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9553    76734441   83  Linux
/dev/sdb2            9554        9964     3301357+   5  Extended
/dev/sdb5            9554        9964     3301326   82  Linux swap / Solaris

Disk /dev/sdc: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7c0a2d96

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        9964    80035798+   7  HPFS/NTFS

---

### Post by jjblackfox on 2008-08-12
> **Cypher said:**
> How old is this computer? Perhaps the hardware is flaky..
My dad built it about 3 months ago. I don't know if he used any old parts though.

---

### Post by NewDisciple on 2008-08-14
From:[http://www.linux-usb.org/]("http://www.linux-usb.org/")
Q:  Why doesn't USB work at all? I get "device not accepting address".

A: This can be one of several problems:

    * High speed devices sometimes have problems with cables used to connect them. They're more sensitive to signal quality issues than older usb 1.1 full or low speed devices. If the device works OK at full speed on the same system, after you "rmmod ehci-hcd", this is likely the problem you're seeing. There are a lot of things you can do to change signal quality.
          o Use a different cable. Some are even marketed specifically for use with high speed devices. Most USB 1.1 cables work just fine at high speed, but the one you're using might be an exception (maybe it's been damaged).
          o Switch to a different USB connector on your computer. Back panel connectors are often right on the motherboard, with much care taken to preserve signal quality. A front panel connector probably doesn't use cabling designed with USB in mind; and its cable could be damaged by bending, baking or something else even when it's not routed through the power supply.
          o Use an external high speed hub. Those hubs have signal conditioning circuitry that may cover up certain flaws.
          o Make sure your device is using its own external power supply, or that its battery is fully charged. 
      You might be able to get the same device to work at high speed on a different machine.
    * You may have some problem with your PCI setup that's preventing your USB host controller from getting hardware interrupts. (Current Linux 2.6 kernels will actually tell you when they notice this problem; see the "dmesg" output.) When Linux submits a request, but never hears back from the controller, this is the diagnostic you'll see. To see if this is the problem, look at /proc/interrupts to see if the interrupt count for your host controller driver ever goes up. If it doesn't, this is the problem: either your BIOS isn't telling the truth to Linux (ACPI sometimes confuses these things, or setting the expected OS to windows in your BIOS), or Linux doesn't understand what it's saying.
    * Sometimes a BIOS fix will be available for your motherboard, and in other cases a more recent kernel will have a Linux fix. You may be able to work around this by passing the noapic boot option to your kernel, or (when you're using an add-in PCI card) moving the USB adapter to some other PCI slot. If you're using a current kernel and BIOS, report this problem to the Linux-kernel mailing list, with details about your motherboard and BIOS.


At the terminal type > dmesg

It should look like this > myname-desktop:~$ dmesg

Then look for /proc/interrupts as stated above.

Also, while in the terminal run > cat /etc/fstab

Post the output from both of these commands here.  I might be able to make some sense out of them.

---

