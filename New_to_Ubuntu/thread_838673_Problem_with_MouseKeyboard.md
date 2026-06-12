---
title: "Problem with Mouse/Keyboard"
date: 2008-06-23
forum: New to Ubuntu
---

### Post by Necro280 on 2008-06-23
Hi! I'm new to Ubuntu :D. I've JUST received and installed it, dual boot now with Vista, it's great! Just, the problem with Ubuntu, is it does not read my mouse and keyboard or something along those lines, I have a Compaq Keyboard, Model #5137
                      and a Compaq Mouse H/P P/N: 5188 - 6231 Rev.A


Their both defaults from my mothers computer, I'm using a HP Pavillion. Could use some help! Thanks!

---

### Post by apjone on 2008-06-23
Hey, can you get to a terminal? if so open a terminal and type 

```

dmesg

```

and paste the bottom 30 lines here.

---

### Post by Necro280 on 2008-06-23
I'd like to use the terminal, i'm using a USB ported mouse/keyboard, wheres the terminal :P?

---

### Post by adobrakic on 2008-06-23
applications > accesories > terminal

---

### Post by Necro280 on 2008-06-23
Ctrl+c = ctr+v does not work

---

### Post by Necro280 on 2008-06-23
55.715562] sd 3:0:0:0: [sda] Write Protect is off
[   55.715563] sd 3:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   55.715574] sd 3:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   55.715577]  sda: sda1 sda2
[   55.724021] sd 3:0:0:0: [sda] Attached SCSI disk
[   56.582189] loop: module loaded
[   56.595079] EXT3-fs: INFO: recovery required on readonly filesystem.
[   56.595083] EXT3-fs: write access will be enabled during recovery.
[   56.663509] kjournald starting.  Commit interval 5 seconds
[   56.663529] EXT3-fs: recovery complete.
[   56.663677] EXT3-fs: mounted filesystem with ordered data mode.
[   58.644777] usb-storage: device scan complete
[   58.651247] scsi 0:0:0:0: Direct-Access     Generic- Compact Flash    1.00 PQ: 0 ANSI: 0 CCS
[   58.657739] scsi 0:0:0:1: Direct-Access     Generic- SM/xD-Picture    1.00 PQ: 0 ANSI: 0 CCS
[   58.664362] scsi 0:0:0:2: Direct-Access     Generic- SD/MMC           1.00 PQ: 0 ANSI: 0 CCS
[   58.671012] scsi 0:0:0:3: Direct-Access     Generic- MS/MS-Pro        1.00 PQ: 0 ANSI: 0 CCS
[   58.672427] sd 0:0:0:0: [sdb] Attached SCSI removable disk
[   58.672461] sd 0:0:0:0: Attached scsi generic sg2 type 0
[   58.673473] sd 0:0:0:1: [sdc] Attached SCSI removable disk
[   58.673500] sd 0:0:0:1: Attached scsi generic sg3 type 0
[   58.674671] sd 0:0:0:2: [sdd] Attached SCSI removable disk
[   58.674706] sd 0:0:0:2: Attached scsi generic sg4 type 0
[   58.675738] sd 0:0:0:3: [sde] Attached SCSI removable disk
[   58.675763] sd 0:0:0:3: Attached scsi generic sg5 type 0
[   61.992191] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x1c00
[   61.992216] i2c-adapter i2c-1: nForce2 SMBus adapter at 0x1c40
[   62.113435] input: Power Button (FF) as /devices/virtual/input/input1
[   62.125687] ACPI: Power Button (FF) [PWRF]
[   62.125771] input: Power Button (CM) as /devices/virtual/input/input2
[   62.141583] ACPI: Power Button (CM) [PWRB]
[   63.690273] ACPI: PCI Interrupt Link [AAZA] enabled at IRQ 22
[   63.690278] ACPI: PCI Interrupt 0000:00:05.0[B] -> Link [AAZA] -> GSI 22 (level, low) -> IRQ 17
[   63.690298] PCI: Setting latency timer of device 0000:00:05.0 to 64
[   63.722965] hda_codec: Unknown model for ALC883, trying auto-probe from BIOS...
[   64.950269] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   64.976020] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   65.032181] Linux agpgart interface v0.102
[   65.663294] input: PC Speaker as /devices/platform/pcspkr/input/input3
[   67.227821] lp: driver loaded but no devices found
[   67.967724] EXT3 FS on loop0, internal journal
[   76.768361] Adding 976552k swap on /host/ubuntu/disks/swap.disk.  Priority:-1 extents:1 across:976552k
[   77.097613] ip_tables: (C) 2000-2006 Netfilter Core Team
[   77.371360] No dock devices found.
[   77.694605] powernow-k8: Found 1 AMD Athlon(tm) 64 X2 Dual Core Processor 4200+ processors (1 cpu cores) (version 2.20.00)
[   77.694643] powernow-k8:    0 : fid 0xe (2200 MHz), vid 0xc
[   77.694645] powernow-k8:    1 : fid 0xc (2000 MHz), vid 0xe
[   77.694647] powernow-k8:    2 : fid 0xa (1800 MHz), vid 0x10
[   77.694649] powernow-k8:    3 : fid 0x2 (1000 MHz), vid 0x12
[   78.339116] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[   78.339121] apm: overridden by ACPI.
[   78.465622] ppdev: user-space parallel port driver
[   78.591106] audit(1214247647.532:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5124 profile="/usr/sbin/cupsd" namespace="default"
[   79.348810] Bluetooth: Core ver 2.11
[   79.349574] NET: Registered protocol family 31
[   79.349577] Bluetooth: HCI device and connection manager initialized
[   79.349581] Bluetooth: HCI socket layer initialized
[   79.382664] Bluetooth: L2CAP ver 2.9
[   79.382669] Bluetooth: L2CAP socket layer initialized
[   79.458893] Bluetooth: RFCOMM socket layer initialized
[   79.459347] Bluetooth: RFCOMM TTY layer initialized
[   79.459350] Bluetooth: RFCOMM ver 1.8
[   98.174387] Clocksource tsc unstable (delta = -90930297 ns)
[  180.290687] NET: Registered protocol family 17
[   84.749890] NET: Registered protocol family 10
[   84.750557] lo: Disabled Privacy Extensions
[  197.036899] eth0: no IPv6 routers present
[  499.133460] usb 1-10: new low speed USB device using ohci_hcd and address 2
[  499.469539] usb 1-10: configuration #1 chosen from 1 choice
[  499.623750] usbcore: registered new interface driver hiddev
[  499.631637] input: Razer Razer 1600dpi Mouse as /devices/pci0000:00/0000:00:02.0/usb1/1-10/1-10:1.0/input/input4
[  499.657324] input,hidraw0: USB HID v1.10 Mouse [Razer Razer 1600dpi Mouse] on usb-0000:00:02.0-10
[  499.657362] usbcore: registered new interface driver usbhid
[  499.657371] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[  547.242618] usb 1-6: new low speed USB device using ohci_hcd and address 3
[  547.456492] usb 1-6: configuration #1 chosen from 1 choice
[  547.473695] input: HID Keyboard Device as /devices/pci0000:00/0000:00:02.0/usb1/1-6/1-6:1.0/input/input5
[  547.498593] input,hidraw1: USB HID v1.10 Keyboard [HID Keyboard Device] on usb-0000:00:02.0-6
[  547.514523] input: HID Keyboard Device as /devices/pci0000:00/0000:00:02.0/usb1/1-6/1-6:1.1/input/input6
[  547.542573] input,hidraw2: USB HID v1.10 Device [HID Keyboard Device] on usb-0000:00:02.0-6

---

### Post by Necro280 on 2008-06-23
Oh, and my mouse/keyboard that arent working are not plugged  in, should i redo it with them in?

---

### Post by Necro280 on 2008-06-23
someone help :P?

---

### Post by stepan2 on 2008-06-23
how is it possible for him to write that message with the keyboard plugged in. I also have a similar problem

---

### Post by Necro280 on 2008-06-24
Lol.. I was able to put in a USB ported Keyboard, and it read!

But unfortunately getting it off my brother is impossible. I need this fixed.

---

### Post by Necro280 on 2008-06-24
Nobody can fix my problem?

---

### Post by Necro280 on 2008-06-24
Someone PLEASE help

---

### Post by Necro280 on 2008-07-10
Still need this answered.

---

### Post by kwag_myers on 2009-12-08
Yes, I realize this thread is more than a year old. But I came upon this thread which describes the exact issue I was having with a Compaq Presario SR2030NX running XP with an AMD 64 processor, only to find no resolution. So...

In my case, I found one of the pins in the [PS2 (Mini-DIN-6)]("http://www.pc-doctors.com/cable-diagrams/keybd.htm#ps2din6") connector of the keyboard was bent. Why that caused the mouse to malfunction is beyond my understanding, but once I straightened out the pin everything worked.

---

