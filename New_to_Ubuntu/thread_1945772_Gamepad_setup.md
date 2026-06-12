---
title: "Gamepad setup"
date: 2012-03-23
forum: New to Ubuntu
---

### Post by jrl1 on 2012-03-23
can anyone help in settng up a Logic 3 usb gamepad in ubuntu 11.10. My system is an alienware amd athlon 4000+ with nvida gforce 7600.

---

### Post by ubudog on 2012-03-23
Should work out-of-the-box (just plug it in); do you get any errors?

Plug it in, and post the output of: 
```
dmesg
```
(run that in a terminal)

Best,
ubudog

---

### Post by jrl1 on 2012-03-23
```

19.275036] Intel ICH 0000:00:04.0: setting latency timer to 64
[   19.447341] init: apport pre-start process (1038) terminated with status 1
[   19.447858] init: alsa-restore main process (1046) terminated with status 19
[   19.480447] ppdev: user-space parallel port driver
[   19.487259] init: apport post-stop process (1069) terminated with status 1
[   19.750520] intel8x0_measure_ac97_clock: measured 191993 usecs (9280 samples)
[   19.750525] intel8x0: clocking to 48000
[   20.020214] ACPI: PCI Interrupt Link [APC3] enabled at IRQ 18
[   20.020237] nvidia 0000:01:00.0: PCI INT A -> Link[APC3] -> GSI 18 (level, low) -> IRQ 18
[   20.020245] nvidia 0000:01:00.0: setting latency timer to 64
[   20.020251] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   20.021295] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  173.14.30  Sat Apr 16 21:49:29 PDT 2011
[   20.185456] skge 0000:05:0c.0: eth0: Link is up at 100 Mbps, full duplex, flow control both
[   20.213256] vesafb: mode is 1024x768x32, linelength=4096, pages=0
[   20.213260] vesafb: scrolling: redraw
[   20.213263] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[   20.213687] vesafb: framebuffer at 0xc0000000, mapped to 0xffffc90011000000, using 3072k, total 3072k
[   20.213902] Console: switching to colour frame buffer device 128x48
[   20.213923] fb0: VESA VGA frame buffer device
[   20.290559] Bluetooth: Core ver 2.16
[   20.290604] NET: Registered protocol family 31
[   20.290605] Bluetooth: HCI device and connection manager initialized
[   20.290609] Bluetooth: HCI socket layer initialized
[   20.290611] Bluetooth: L2CAP socket layer initialized
[   20.293066] Bluetooth: SCO socket layer initialized
[   20.331268] Bluetooth: RFCOMM TTY layer initialized
[   20.331277] Bluetooth: RFCOMM socket layer initialized
[   20.331279] Bluetooth: RFCOMM ver 1.11
[   20.371991] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   20.371995] Bluetooth: BNEP filters: protocol multicast
[   21.746382] EXT4-fs (sdb5): re-mounted. Opts: errors=remount-ro,commit=0
[   21.899133] init: plymouth-stop pre-start process (1294) terminated with status 1
[   23.404524] EXT4-fs (sdb5): re-mounted. Opts: errors=remount-ro,commit=0
[   29.104025] eth0: no IPv6 routers present

```

---

### Post by ubudog on 2012-03-23
Hmm, could you run:
```
lsusb
```
and post the output?  (while the gamepad is plugged in)

---

### Post by jrl1 on 2012-03-23
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 11b0:6208 ATECH FLASH TECHNOLOGY 
Bus 002 Device 002: ID 04b8:0883 Seiko Epson Corp. 
Bus 002 Device 003: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 002 Device 004: ID 12bd:d014

---

### Post by ubudog on 2012-03-23
Have you tried playing any games with it yet?

---

### Post by jrl1 on 2012-03-23
when i play games the option for using a gamepad isn't there. only for using keyboard and mouse. However the system is dual booted with windows xp where i am able to configure the gamepad with no problem

---

### Post by Grumbel on 2012-03-27
Normally gamepads work in Linux out-of-the-box, you plug them in and they work. To see if Linux picked it up properly, have a look at /dev/input/, there should be a file /dev/input/js0, run jstest on that file (install 'joystick' package if you haven't already):

  jstest /dev/input/js0

If the file is missing, then there is a problem, you could try (your last dmesg doesn't have joystick info, but that might be a copy&paste error):

1) unplug you gamepad
2) boot Linux
3) run "dmesg -c"
4) plug in your gamepad
5) run dmesg without the -c and post output here

In general just unplug it and replug it in, see what dmesg has to say about that.

If jstest picks up your gamepad, but the game doesn't, then it's a problem with the game, not the gamepad, thus tell us what games you are trying to play.

---

