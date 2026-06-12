---
title: "Sound Problems in Ubuntu"
date: 2008-05-05
forum: New to Ubuntu
---

### Post by Eisenhemm on 2008-05-05
Hello All,
I am dual booting ubuntu and vista.
I have some  sound problems in ubuntu. When i boot ubuntu there seem to be no sound in  that but  when i hibernate it and again start ...the sound works properly. Sound goes off again if i boot vista then reboot ubuntu.
Kindly suggest a solution for the same.

Thank You

---

### Post by hermes0710 on 2008-05-05
Can you post the last 30-40 lines of the output of "dmesg"? What is your soundcard's model?

---

### Post by Eisenhemm on 2008-05-05
The following is the last few lines of the output to the cammand dmesg :---

[   22.280000] ACPI: AC Adapter [ADP1] (off-line)
[   22.292000] EXT3 FS on sda2, internal journal
[   22.348000] sky2 eth0: Link is up at 100 Mbps, full duplex, flow control both
[   22.352000] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   23.224000] ipw3945: Radio Frequency Kill Switch is On:
[   23.224000] Kill switch must be turned off for wireless networking to work.
[   23.480000] audit(1210043046.176:3):  type=1505 operation="profile_load" info="failed to unpack profile" name="/usr/lib/cups/backend/cups-pdf" pid=4371
[   23.672000] ip_tables: (C) 2000-2006 Netfilter Core Team
[   25.844000] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   25.852000] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   25.916000] ACPI: Battery Slot [BAT0] (battery present)
[   25.932000] input: Power Button (FF) as /class/input/input5
[   25.932000] ACPI: Power Button (FF) [PWRF]
[   25.932000] input: Lid Switch as /class/input/input6
[   25.932000] ACPI: Lid Switch [LID0]
[   25.932000] input: Sleep Button (CM) as /class/input/input7
[   25.932000] ACPI: Sleep Button (CM) [SLPB]
[   26.012000] No dock devices found.
[   28.100000] Failure registering capabilities with primary security module.
[   28.296000] ppdev: user-space parallel port driver
[   28.520000] apm: BIOS not found.
[   28.840000] Installing knfsd (copyright (C) 1996 [email]okir@monad.swb.de[/email]).
[   28.892000] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
[   28.908000] NFSD: starting 90-second grace period
[   30.208000] Bluetooth: Core ver 2.11
[   30.208000] NET: Registered protocol family 31
[   30.208000] Bluetooth: HCI device and connection manager initialized
[   30.208000] Bluetooth: HCI socket layer initialized
[   30.240000] Bluetooth: L2CAP ver 2.8
[   30.240000] Bluetooth: L2CAP socket layer initialized
[   30.328000] Bluetooth: RFCOMM socket layer initialized
[   30.328000] Bluetooth: RFCOMM TTY layer initialized
[   30.328000] Bluetooth: RFCOMM ver 1.8
[   33.980000] [drm] Initialized drm 1.1.0 20060810
[   34.012000] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 17
[   34.012000] [drm] Initialized i915 1.6.0 20060119 on minor 0
[  879.360000] sky2 eth0: Link is down.
[  881.104000] sky2 eth0: Link is up at 100 Mbps, full duplex, flow control both





The Output to the command aplay -l is :-

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: Conexant Digital [Conexant Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

