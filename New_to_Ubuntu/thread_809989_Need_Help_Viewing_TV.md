---
title: "Need Help Viewing TV"
date: 2008-05-27
forum: New to Ubuntu
---

### Post by newby1980 on 2008-05-27
I need help viewing TV in ubuntu.  My media player is gxine and I am pretty sure Ubuntu recognizes my card here is dmesg:

[  717.793330] cx88/2: cx2388x dvb driver version 0.0.6 loaded
[  717.793342] cx88/2: registering cx8802 driver, type: dvb access: shared
[  717.793348] cx88[0]/2: subsystem: 1043:4823, board: ASUS PVR-416 [card=12]
[  717.793353] cx88[0]/2: cx8802 probe failed, err = -19
[  856.026065] cx88/2: cx2388x dvb driver version 0.0.6 loaded
[  856.026074] cx88/2: registering cx8802 driver, type: dvb access: shared
[  856.026081] cx88[0]/2: subsystem: 1043:4823, board: ASUS PVR-416 [card=12]
[  856.026086] cx88[0]/2: cx8802 probe failed, err = -19


There is also an previous entry:

[   64.681341] cx88[0]/2-bb: Firmware and/or mailbox pointer not initialized or corrupted
[   67.434693] cx88[0]/2-bb: Firmware upload successful.
[   67.442554] cx88[0]/2-bb: Firmware version is 0x02060039
[   67.504842] cx88[0]/2-bb: VIDIOC_TRY_FMT: w: 720, h: 480, f: 4

And even another one:

 46.052007] cx88[0]: subsystem: 1043:4823, board: ASUS PVR-416 [card=12,autodetected]
[   46.052012] cx88[0]: TV tuner type 43, Radio tuner type -1
[   46.129508] lirc_dev: lirc_register_plugin: sample_rate: 0
[   46.133501] lirc_mceusb2[2]: Mitsumi eHome Infrared Transceiver on usb4:2
[   46.133540] usbcore: registered new interface driver lirc_mceusb2
[   46.205075] cx88[0]/2: cx2388x 8802 Driver Manager
[   46.205099] ACPI: PCI Interrupt 0000:02:04.2[A] -> GSI 16 (level, low) -> IRQ 16
[   46.205113] cx88[0]/2: found at 0000:02:04.2, rev: 5, irq: 16, latency: 64, mmio: 0xce000000
[   46.205175] ACPI: PCI Interrupt 0000:02:04.0[A] -> GSI 16 (level, low) -> IRQ 16
[   46.205187] cx88[0]/0: found at 0000:02:04.0, rev: 5, irq: 16, latency: 64, mmio: 0xcd000000
[   46.291908] tuner 0-0043: chip found @ 0x86 (cx88[0])
[   46.291941] tda9887 0-0043: tda988[5/6/7] found @ 0x43 (tuner)
[   46.291945] tuner 0-0043: type set to tda9887
[   46.294288] All bytes are equal. It is not a TEA5767
[   46.294292] tuner 0-0060: chip found @ 0xc0 (cx88[0])
[   46.294315] tuner-simple 0-0060: type set to 43 (Philips NTSC MK3 (FM1236MK3 or FM1236/F))
[   46.294320] tuner 0-0060: type set to Philips NTSC MK3 (F
[   46.294324] tuner-simple 0-0060: type set to 43 (Philips NTSC MK3 (FM1236MK3 or FM1236/F))
[   46.294329] tuner 0-0060: type set to Philips NTSC MK3 (F
[   46.302864] cx88[0]/0: registered device video0 [v4l2]
[   46.302899] cx88[0]/0: registered device vbi0
[   46.302929] cx88[0]/0: registered device radio0
[   46.344059] cx2388x blackbird driver version 0.0.6 loaded
[   46.344066] cx88/2: registering cx8802 driver, type: blackbird access: shared
[   46.344074] cx88[0]/2: subsystem: 1043:4823, board: ASUS PVR-416 [card=12]
[   46.344080] cx88[0]/2: cx23416 based mpeg encoder (blackbird reference design)
[   46.344356] cx88[0]/2: registered device video1 [mpeg]


And even one more but I think this should suffice.

Any help would be appreciated.

Ubuntu 8.04 (hardy)
GNOME 2.22.2
Kernel 2.6.24-17-generic
Intel Pentium 4 3Ghz
1 GB RAm

:mad:

---

### Post by quelx on 2008-05-27
Have you tried using **xawtv** or **tvtime** to view the tuner card?

---

### Post by newby1980 on 2008-05-28
Tvtime yes xawtv no

If i knew the parameters that might help
:confused:

---

### Post by quelx on 2008-05-28
What kind of TV card is it exactly? Here is a list of supported cards for what the kernel seems to think it is: [http://linuxtv.org/hg/v4l-dvb?cmd=file;file=linux/Documentation/video4linux/CARDLIST.cx88;filenode=-1;style=raw](http://linuxtv.org/hg/v4l-dvb?cmd=file;file=linux/Documentation/video4linux/CARDLIST.cx88;filenode=-1;style=raw)

You may need just a bit more tweaking to make sure it's detected properly

---

