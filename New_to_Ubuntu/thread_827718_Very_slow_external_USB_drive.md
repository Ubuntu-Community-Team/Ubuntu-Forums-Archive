---
title: "Very slow external USB drive"
date: 2008-06-13
forum: New to Ubuntu
---

### Post by vhadiant on 2008-06-13
Hi,

I have a 500GB external drive that is doing fine under Windows XP but really slow when I plug it in to Ubuntu. How do I diagnose this problem? Maybe it's using USB 1 protocol or something?

---

### Post by vhadiant on 2008-06-13
Bump ... anyone?

---

### Post by alienexplorers on 2008-06-14
What type of USB port do you have.  Is it 1.0 or 2.0..... If 1.0 then I would get a 2.0 port card and use that.

---

### Post by vhadiant on 2008-06-14
I'm sure it's 2.0. This drive works fine & quite fast in Windows but having trouble in Ubuntu.

---

### Post by ukripper on 2008-06-14
> **vhadiant said:**
> Bump ... anyone?

Cab you disconnect and reconnect your usb and post output of the following:
```
lsusb
```

---

### Post by vhadiant on 2008-06-14
I have this:


```
Bus 005 Device 005: ID 059f:0651 LaCie, Ltd 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 04f3:0212 Elan Microelectronics Corp. 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 007: ID 0b97:7762 O2 Micro, Inc. Oz776 SmartCard Reader
Bus 001 Device 006: ID 413c:8126 Dell Computer Corp. 
Bus 001 Device 005: ID 0b97:7761 O2 Micro, Inc. 
Bus 001 Device 004: ID 413c:a005 Dell Computer Corp. 
Bus 001 Device 001: ID 0000:0000  
```

---

### Post by ukripper on 2008-06-14
Can you also post output of the following command:
```
lsusb -v
``` to find it whether is running on full speed 
and for any errors can you post:
```
dmesg | tail
```

---

### Post by vhadiant on 2008-06-14
The lsubs -v command returns this:

Bus 005 Device 005: ID 059f:0651 LaCie, Ltd 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x059f LaCie, Ltd
  idProduct          0x0651 
  bcdDevice            0.00
  iManufacturer           1 LaCie
  iProduct                2 LaCie Hard Drive USB
  iSerial                 3 10000E000CF4C6CC
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           32
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xc0
      Self Powered
    MaxPower                2mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass         8 Mass Storage
      bInterfaceSubClass      6 SCSI
      bInterfaceProtocol     80 Bulk (Zip)
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
Device Qualifier (for other device speed):
  bLength                10
  bDescriptorType         6
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  bNumConfigurations      1
Device Status:     0x0001
  Self Powered

And dmesg:

[CODE]
[ 1834.868296] sd 3:0:0:0: [sdb] Write Protect is off
[ 1834.868303] sd 3:0:0:0: [sdb] Mode Sense: 53 00 00 08
[ 1834.868307] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[ 1834.869662] sd 3:0:0:0: [sdb] 976773168 512-byte hardware sectors (500108 MB)
[ 1834.870538] sd 3:0:0:0: [sdb] Write Protect is off
[ 1834.870543] sd 3:0:0:0: [sdb] Mode Sense: 53 00 00 08
[ 1834.870546] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[ 1834.870551]  sdb: sdb1
[ 1834.892392] sd 3:0:0:0: [sdb] Attached SCSI disk
[ 1834.892460] sd 3:0:0:0: Attached scsi generic sg2 type 0
[CODE]

So I think it's ok but when I transfer file to it (not reading) it's really slow.

---

### Post by ukripper on 2008-06-14
can you do following to find if your usb hub supports the high speed device.
```
lspci
```

---

### Post by vhadiant on 2008-06-14
I'm sure it is. It's a 1.5 years old Dell M1710 laptop.

Anyway the lspci command shows this:

```

victorh@victorlappy:~$ sudo lspci
[sudo] password for victorh: 
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation GeForce Go 7900 GTX (rev a1)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
03:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
03:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
09:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5752 Gigabit Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
victorh@victorlappy:~$ 

```

---

### Post by ukripper on 2008-06-14
> **vhadiant said:**
> (rev 01)
[B]00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI[/B] Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)


As you can see from the output four controllers are UHCI which means using usb 1.1 not 2.0. This means if you attached your USB drive to any of these controllers you won't get high speed transfer rate and on the other hand if you look at you have one controller which is  USB EHCI if you connect your USB drive to that you should get high speed transfer rate.

---

### Post by vhadiant on 2008-06-14
> **ukripper said:**
> As you can see from the output four controllers are UHCI which means using usb 1.1 not 2.0. This means if you attached your USB drive to any of these controllers you won't get high speed transfer rate and on the other hand if you look at you have one controller which is  USB EHCI if you connect your USB drive to that you should get high speed transfer rate.

Hmm that's odd ... because, in Windows I plugged it into the same USB drive and it's OK. I remember I had to install a special driver for these USB controllers to USB2. Is there similar things with Linux?

I'm I'm quite certain I wasn't running it in USB 1 mode in Windows, although now it make sense why it's really slow in Ubuntu.

---

### Post by ukripper on 2008-06-14
can do one more thing to be certain:
post following command's output:
```
dmesg | grep usb
```

post it using code when using reply

---

### Post by vhadiant on 2008-06-14
Here it is:

```

[   11.958608] usbcore: registered new interface driver usbfs
[   11.958627] usbcore: registered new interface driver hub
[   11.967067] usbcore: registered new device driver usb
[   11.980044] usb usb1: configuration #1 chosen from 1 choice
[   12.082631] usb usb2: configuration #1 chosen from 1 choice
[   14.023225] usb usb3: configuration #1 chosen from 1 choice
[   14.128085] usb usb4: configuration #1 chosen from 1 choice
[   14.159794] usb 1-1: new full speed USB device using uhci_hcd and address 2
[   14.283341] usb usb5: configuration #1 chosen from 1 choice
[   12.523768] usb 1-1: device not accepting address 2, error -71
[   14.847196] usb 5-7: new high speed USB device using ehci_hcd and address 4
[   13.143158] usb 5-7: configuration #1 chosen from 1 choice
[   13.381058] usb 1-1: new full speed USB device using uhci_hcd and address 4
[   13.517280] usb 1-1: configuration #1 chosen from 1 choice
[   15.698955] usb 3-1: new low speed USB device using uhci_hcd and address 2
[   14.027280] usb 3-1: configuration #1 chosen from 1 choice
[   16.082852] usb 1-1.2: new full speed USB device using uhci_hcd and address 5
[   16.208623] usb 1-1.2: configuration #1 chosen from 1 choice
[   14.704498] usb 1-1.4: new full speed USB device using uhci_hcd and address 6
[   14.848122] usb 1-1.4: configuration #1 chosen from 1 choice
[   15.054242] usb 1-1.2.2: new full speed USB device using uhci_hcd and address 7
[   15.168602] usb 1-1.2.2: configuration #1 chosen from 1 choice
[   22.680816] usbcore: registered new interface driver libusual
[   24.523551] usbcore: registered new interface driver hiddev
[   24.536682] input: PS/2+USB Mouse as /devices/pci0000:00/0000:00:1d.2/usb3/3-1/3-1:1.0/input/input8
[   22.996590] usb-storage: device found at 4
[   22.996592] usb-storage: waiting for device to settle before scanning
[   24.836819] input,hidraw0: USB HID v1.11 Mouse [PS/2+USB Mouse] on usb-0000:00:1d.2-1
[   24.836840] usbcore: registered new interface driver usbhid
[   24.836843] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   24.838511] usbcore: registered new interface driver hci_usb
[   23.003064] usbcore: registered new interface driver usb-storage
[   27.339103] usb-storage: device scan complete

```

---

### Post by ukripper on 2008-06-14
> **vhadiant said:**
> 
**[   14.159794] usb 1-1: new full speed USB device using uhci_hcd and address 2**
[   14.283341] usb usb5: configuration #1 chosen from 1 choice
[   12.523768] usb 1-1: device not accepting address 2, error -71
**[   14.847196] usb 5-7: new high speed USB device using ehci_hcd and address 4**
As you can see from above your one of the full speed device is using UHCI this could probably be your drive.

Can you try swapping usb ports and see where you get the best transfer rate and you can use that usb port for your drive.

As you already have ehci controller detected and some device is already using it:
> new high speed USB device using ehci_hcd and address 4

lets see full output of your dmesg and find out:
```
dmesg
```

post output

---

### Post by vhadiant on 2008-06-14
This is what I did. I unplugged both my mouse & external USB drive. Then plugged in the external USB drive:

dmesg | grep usb gives me this:

```

[   22.138386] usbcore: registered new interface driver usbfs
[   22.138406] usbcore: registered new interface driver hub
[   22.138430] usbcore: registered new device driver usb
[   22.140004] usb usb1: configuration #1 chosen from 1 choice
[   22.240417] usb usb2: configuration #1 chosen from 1 choice
[   22.344289] usb usb3: configuration #1 chosen from 1 choice
[   22.448127] usb usb4: configuration #1 chosen from 1 choice
[   20.643112] usb 1-1: new full speed USB device using uhci_hcd and address 2
[   20.771029] usb usb5: configuration #1 chosen from 1 choice
[   20.955194] usb 1-1: device not accepting address 2, error -71
[   21.494641] usb 5-7: new high speed USB device using ehci_hcd and address 4
[   21.627483] usb 5-7: configuration #1 chosen from 1 choice
[   21.860555] usb 1-1: new full speed USB device using uhci_hcd and address 4
[   22.006954] usb 1-1: configuration #1 chosen from 1 choice
[   24.191928] usb 3-1: new low speed USB device using uhci_hcd and address 2
[   22.517327] usb 3-1: configuration #1 chosen from 1 choice
[   24.577400] usb 1-1.2: new full speed USB device using uhci_hcd and address 5
[   22.864862] usb 1-1.2: configuration #1 chosen from 1 choice
[   23.193609] usb 1-1.4: new full speed USB device using uhci_hcd and address 6
[   23.336788] usb 1-1.4: configuration #1 chosen from 1 choice
[   23.541601] usb 1-1.2.2: new full speed USB device using uhci_hcd and address 7
[   23.657177] usb 1-1.2.2: configuration #1 chosen from 1 choice
[   30.992931] usbcore: registered new interface driver hiddev
[   31.017354] input: PS/2+USB Mouse as /devices/pci0000:00/0000:00:1d.2/usb3/3-1/3-1:1.0/input/input8
[   31.318904] input,hidraw0: USB HID v1.11 Mouse [PS/2+USB Mouse] on usb-0000:00:1d.2-1
[   31.318929] usbcore: registered new interface driver usbhid
[   31.318933] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   31.367317] usbcore: registered new interface driver hci_usb
[   31.379718] usbcore: registered new interface driver libusual
[   33.237171] usbcore: registered new interface driver usb-storage
[   31.397511] usb-storage: device found at 4
[   31.397513] usb-storage: waiting for device to settle before scanning
[   35.714508] usb-storage: device scan complete
[  100.939539] usb 3-1: USB disconnect, address 2
[  106.522377] usb 5-7: USB disconnect, address 4
[  109.544988] usb 5-5: new high speed USB device using ehci_hcd and address 5
[  109.677788] usb 5-5: configuration #1 chosen from 1 choice
[  109.678693] usb-storage: device found at 5
[  109.678701] usb-storage: waiting for device to settle before scanning
[  110.716977] usb-storage: device scan complete

```

So it looks like that my external drive is using USB 2. Is this correct?

When I plugged in my mouse:

```

[  138.709773] usb 4-1: new low speed USB device using uhci_hcd and address 2
[  136.891412] usb 4-1: configuration #1 chosen from 1 choice
[  138.749060] input: PS/2+USB Mouse as /devices/pci0000:00/0000:00:1d.3/usb4/4-1/4-1:1.0/input/input9
[  136.950744] input,hidraw0: USB HID v1.11 Mouse [PS/2+USB Mouse] on usb-0000:00:1d.3-1

```

So it looks like the USB drive is USB2 and the mouse is USB 1. Strange that my drive is running like a dog.

---

### Post by ukripper on 2008-06-14
can you post output of ```
dmesg 
```command

full output

---

### Post by vhadiant on 2008-06-14
Rebooted my box again. Here is the dmesg output:

```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.24-18-generic (buildd@terranova) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Wed May 28 20:27:26 UTC 2008 (Ubuntu 2.6.24-18.32-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
[    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007fed9c00 (usable)
[    0.000000]  BIOS-e820: 000000007fed9c00 - 0000000080000000 (reserved)
[    0.000000]  BIOS-e820: 00000000f0000000 - 00000000f4007000 (reserved)
[    0.000000]  BIOS-e820: 00000000f4008000 - 00000000f400c000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed20000 - 00000000feda0000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee10000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
[    0.000000] 1150MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 523993) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   523993
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   523993
[    0.000000] On node 0 totalpages: 523993
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2301 pages used for memmap
[    0.000000]   HighMem zone: 292316 pages, LIFO batch:31
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] DMI 2.4 present.
[    0.000000] ACPI: RSDP signature @ 0xC00FC1D0 checksum 0
[    0.000000] ACPI: RSDP 000FC1D0, 0014 (r0 DELL  )
[    0.000000] ACPI: RSDT 7FEDA18A, 0044 (r1 DELL    M07     27D70402 ASL        61)
[    0.000000] ACPI: FACP 7FEDB000, 0074 (r1 DELL    M07     27D70402 ASL        61)
[    0.000000] ACPI: DSDT 7FEDBC00, 4B19 (r1 INT430 SYSFexxx     1001 INTL 20050624)
[    0.000000] ACPI: FACS 7FEEA400, 0040
[    0.000000] ACPI: HPET 7FEDB700, 0038 (r1 DELL    M07            1 ASL        61)
[    0.000000] ACPI: APIC 7FEDB800, 0068 (r1 DELL    M07     27D70402 ASL        47)
[    0.000000] ACPI: MCFG 7FEDB7C0, 003E (r16 DELL    M07     27D70402 ASL        61)
[    0.000000] ACPI: SLIC 7FEDB89C, 0176 (r1 DELL    M07     27D70402 ASL        61)
[    0.000000] ACPI: OSFR 7FEDAE00, 002C (r1 DELL    M07     27D70402 ASL        61)
[    0.000000] ACPI: BOOT 7FEDB3C0, 0028 (r1 DELL    M07     27D70402 ASL        61)
[    0.000000] ACPI: SSDT 7FEDA211, 04DC (r1  PmRef    CpuPm     3000 INTL 20050624)
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 6:15 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] Processor #1 6:15 APIC version 20
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:70000000)
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 0000000000100000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 519900
[    0.000000] Kernel command line: root=UUID=5bfb8105-29f7-4b34-895f-70a228a50318 ro quiet splash
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 1997.390 MHz processor.
[    8.120619] Console: colour VGA+ 80x25
[    8.120623] console [tty0] enabled
[    8.120893] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    8.121160] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    8.201560] Memory: 2065948k/2095972k available (2176k kernel code, 28704k reserved, 1006k data, 368k init, 1178468k highmem)
[    8.201566] virtual kernel memory layout:
[    8.201567]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[    8.201568]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    8.201569]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[    8.201570]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[    8.201571]       .init : 0xc0421000 - 0xc047d000   ( 368 kB)
[    8.201571]       .data : 0xc03201f4 - 0xc041bdc4   (1006 kB)
[    8.201572]       .text : 0xc0100000 - 0xc03201f4   (2176 kB)
[    8.201575] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[    8.201615] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[    8.201746] hpet clockevent registered
[    8.281645] Calibrating delay using timer specific routine.. 3998.82 BogoMIPS (lpj=7997648)
[    8.281666] Security Framework initialized
[    8.281672] SELinux:  Disabled at boot.
[    8.281685] AppArmor: AppArmor initialized
[    8.281688] Failure registering capabilities with primary security module.
[    8.281696] Mount-cache hash table entries: 512
[    8.281816] Initializing cgroup subsys ns
[    8.281822] Initializing cgroup subsys cpuacct
[    8.281831] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e3bd 00000000 00000001 00000000
[    8.281838] monitor/mwait feature present.
[    8.281839] using mwait in idle threads.
[    8.281843] CPU: L1 I cache: 32K, L1 D cache: 32K
[    8.281845] CPU: L2 cache: 4096K
[    8.281848] CPU: Physical Processor ID: 0
[    8.281849] CPU: Processor Core ID: 0
[    8.281851] CPU: After all inits, caps: bfebfbff 20100000 00000000 00003940 0000e3bd 00000000 00000001 00000000
[    8.281859] Compat vDSO mapped to ffffe000.
[    8.281871] Checking 'hlt' instruction... OK.
[    8.297977] SMP alternatives: switching to UP code
[    8.299437] Early unpacking initramfs... done
[    8.586539] ACPI: Core revision 20070126
[    8.586576] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[    8.589044] CPU0: Intel(R) Core(TM)2 CPU         T7200  @ 2.00GHz stepping 06
[    8.589058] SMP alternatives: switching to SMP code
[    8.589703] Booting processor 1/1 eip 3000
[   10.439551] Initializing CPU#1
[   10.518155] Calibrating delay using timer specific routine.. 3994.69 BogoMIPS (lpj=7989392)
[   10.518161] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e3bd 00000000 00000001 00000000
[   10.518165] monitor/mwait feature present.
[   10.518168] CPU: L1 I cache: 32K, L1 D cache: 32K
[   10.518170] CPU: L2 cache: 4096K
[   10.518172] CPU: Physical Processor ID: 0
[   10.518173] CPU: Processor Core ID: 1
[   10.518174] CPU: After all inits, caps: bfebfbff 20100000 00000000 00003940 0000e3bd 00000000 00000001 00000000
[    8.681849] CPU1: Intel(R) Core(TM)2 CPU         T7200  @ 2.00GHz stepping 06
[    8.681869] Total of 2 processors activated (7993.52 BogoMIPS).
[    8.682062] ENABLING IO-APIC IRQs
[    8.682246] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[    8.829005] checking TSC synchronization [CPU#0 -> CPU#1]:
[    8.848985] Measured 3674103732 cycles TSC warp between CPUs, turning off TSC clock.
[    8.848987] Marking TSC unstable due to: check_tsc_sync_source failed.
[    8.848999] Brought up 2 CPUs
[    8.849021] CPU0 attaching sched-domain:
[    8.849024]  domain 0: span 03
[    8.849025]   groups: 01 02
[    8.849028] CPU1 attaching sched-domain:
[    8.849029]  domain 0: span 03
[    8.849031]   groups: 02 01
[   10.686299] net_namespace: 64 bytes
[   10.686309] Booting paravirtualized kernel on bare hardware
[   10.686717] Time: 18:35:32  Date: 06/14/08
[   10.686741] NET: Registered protocol family 16
[   10.686924] EISA bus registered
[   10.686929] ACPI: bus type pci registered
[   10.715107] PCI: PCI BIOS revision 2.10 entry at 0xfb016, last bus=14
[   10.715109] PCI: Using configuration type 1
[   10.715111] Setting up standard PCI resources
[    8.883101] ACPI: EC: Look up EC in DSDT
[    8.893868] ACPI: SSDT 7FEDA1CE, 0043 (r1  LMPWR  DELLLOM     1001 INTL 20050624)
[    8.894001] ACPI: Interpreter enabled
[    8.894004] ACPI: (supports S0 S3 S4 S5)
[    8.894016] ACPI: Using IOAPIC for interrupt routing
[    8.909640] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    8.910421] PCI quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[    8.910425] PCI quirk: region 1080-10bf claimed by ICH6 GPIO
[    8.911893] PCI: Transparent bridge - 0000:00:1e.0
[    8.911942] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    8.912265] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[    8.912342] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIE._PRT]
[    8.912474] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    8.912570] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[    8.912665] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PXP0._PRT]
[    8.912730] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP04._PRT]
[    8.930163] ACPI: PCI Interrupt Link [LNKA] (IRQs *9 10 11)
[    8.930256] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 7) *3
[    8.930347] ACPI: PCI Interrupt Link [LNKC] (IRQs 9 10 11) *5
[    8.930437] ACPI: PCI Interrupt Link [LNKD] (IRQs 5 7 9 10 *11)
[    8.930528] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[    8.930620] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[    8.930713] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[    8.930805] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
[    8.930936] Linux Plug and Play Support v0.97 (c) Adam Belay
[    8.930965] pnp: PnP ACPI init
[    8.930972] ACPI: bus type pnp registered
[    8.945021] pnpacpi: exceeded the max number of mem resources: 12
[    8.959107] pnp: PnP ACPI: found 12 devices
[    8.959109] ACPI: ACPI bus type pnp unregistered
[    8.959112] PnPBIOS: Disabled by ACPI PNP
[   10.796381] PCI: Using ACPI for IRQ routing
[   10.796383] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   10.877789] NET: Registered protocol family 8
[   10.877790] NET: Registered protocol family 20
[   10.877821] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[   10.877825] hpet0: 3 64-bit timers, 14318180 Hz
[   10.878853] AppArmor: AppArmor Filesystem Enabled
[    9.044618] Time: hpet clocksource has been installed.
[    9.044633] Switched to high resolution mode on CPU 0
[   10.881784] Switched to high resolution mode on CPU 1
[    9.057600] system 00:00: iomem range 0x0-0x9fbff could not be reserved
[    9.057603] system 00:00: iomem range 0x9fc00-0x9ffff could not be reserved
[    9.057605] system 00:00: iomem range 0xc0000-0xcffff could not be reserved
[    9.057607] system 00:00: iomem range 0xe0000-0xfffff could not be reserved
[    9.057610] system 00:00: iomem range 0x100000-0x7fed9bff could not be reserved
[    9.057612] system 00:00: iomem range 0x7fed9c00-0x7fefffff could not be reserved
[    9.057615] system 00:00: iomem range 0x7ff00000-0x7fffffff could not be reserved
[    9.057617] system 00:00: iomem range 0xffb00000-0xffffffff could not be reserved
[    9.057619] system 00:00: iomem range 0xfec00000-0xfec0ffff could not be reserved
[    9.057622] system 00:00: iomem range 0xfee00000-0xfee0ffff could not be reserved
[    9.057624] system 00:00: iomem range 0xfed20000-0xfed9ffff could not be reserved
[    9.057627] system 00:00: iomem range 0xffa80000-0xffa83fff could not be reserved
[    9.057633] system 00:02: ioport range 0x4d0-0x4d1 has been reserved
[    9.057635] system 00:02: ioport range 0x1000-0x1005 has been reserved
[    9.057637] system 00:02: ioport range 0x1008-0x100f has been reserved
[    9.057642] system 00:03: ioport range 0xf400-0xf4fe has been reserved
[    9.057645] system 00:03: ioport range 0x1006-0x1007 has been reserved
[    9.057647] system 00:03: ioport range 0x100a-0x1059 could not be reserved
[    9.057649] system 00:03: ioport range 0x1060-0x107f has been reserved
[    9.057651] system 00:03: ioport range 0x1080-0x10bf has been reserved
[    9.057653] system 00:03: ioport range 0x10c0-0x10df has been reserved
[    9.057655] system 00:03: ioport range 0x1010-0x102f has been reserved
[    9.057658] system 00:03: ioport range 0x809-0x809 has been reserved
[    9.057665] system 00:08: ioport range 0xc80-0xcff could not be reserved
[    9.057667] system 00:08: ioport range 0x910-0x91f has been reserved
[    9.057669] system 00:08: ioport range 0x920-0x92f has been reserved
[    9.057671] system 00:08: ioport range 0xcb0-0xcbf has been reserved
[    9.057673] system 00:08: ioport range 0x930-0x97f has been reserved
[    9.057679] system 00:0b: iomem range 0xfed00000-0xfed003ff has been reserved
[    9.088058] PCI: Bridge: 0000:00:01.0
[    9.088060]   IO window: e000-efff
[    9.088064]   MEM window: ed000000-efefffff
[    9.088066]   PREFETCH window: d0000000-dfffffff
[    9.088070] PCI: Bridge: 0000:00:1c.0
[    9.088071]   IO window: disabled.
[    9.088076]   MEM window: disabled.
[    9.088080]   PREFETCH window: disabled.
[    9.088085] PCI: Bridge: 0000:00:1c.1
[    9.088087]   IO window: disabled.
[    9.088092]   MEM window: ecf00000-ecffffff
[    9.088096]   PREFETCH window: disabled.
[    9.088101] PCI: Bridge: 0000:00:1c.2
[    9.088102]   IO window: disabled.
[    9.088108]   MEM window: ece00000-ecefffff
[    9.088111]   PREFETCH window: disabled.
[    9.088117] PCI: Bridge: 0000:00:1c.3
[    9.088119]   IO window: d000-dfff
[    9.088125]   MEM window: ecc00000-ecdfffff
[    9.088129]   PREFETCH window: e0000000-e01fffff
[    9.088135] PCI: Bridge: 0000:00:1e.0
[    9.088136]   IO window: disabled.
[    9.088141]   MEM window: ecb00000-ecbfffff
[    9.088145]   PREFETCH window: disabled.
[    9.088161] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 16
[    9.088165] PCI: Setting latency timer of device 0000:00:01.0 to 64
[    9.088186] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 16
[    9.088192] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[    9.088214] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 17 (level, low) -> IRQ 17
[    9.088219] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[    9.088242] ACPI: PCI Interrupt 0000:00:1c.2[C] -> GSI 18 (level, low) -> IRQ 18
[    9.088247] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[    9.088270] ACPI: PCI Interrupt 0000:00:1c.3[D] -> GSI 19 (level, low) -> IRQ 19
[    9.088275] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[    9.088288] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[    9.088298] NET: Registered protocol family 2
[    9.132510] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    9.132692] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    9.133064] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    9.133243] TCP: Hash tables configured (established 131072 bind 65536)
[    9.133245] TCP reno registered
[    9.144559] checking if image is initramfs... it is
[    9.709004] Freeing initrd memory: 7320k freed
[    9.709159] Simple Boot Flag at 0x79 set to 0x1
[   11.546864] audit: initializing netlink socket (disabled)
[   11.546878] audit(1213468532.384:1): initialized
[    9.710041] highmem bounce pool size: 64 pages
[    9.711927] VFS: Disk quotas dquot_6.5.1
[    9.711995] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    9.712113] io scheduler noop registered
[    9.712115] io scheduler anticipatory registered
[    9.712117] io scheduler deadline registered
[    9.712126] io scheduler cfq registered (default)
[    9.712234] Boot video device is 0000:01:00.0
[    9.712339] PCI: Setting latency timer of device 0000:00:01.0 to 64
[    9.712374] assign_interrupt_mode Found MSI capability
[    9.712403] Allocate Port Service[0000:00:01.0:pcie00]
[    9.712480] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[    9.712536] assign_interrupt_mode Found MSI capability
[    9.712580] Allocate Port Service[0000:00:1c.0:pcie00]
[    9.712614] Allocate Port Service[0000:00:1c.0:pcie02]
[    9.712715] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[    9.712771] assign_interrupt_mode Found MSI capability
[    9.712816] Allocate Port Service[0000:00:1c.1:pcie00]
[    9.712847] Allocate Port Service[0000:00:1c.1:pcie02]
[    9.712946] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[    9.713001] assign_interrupt_mode Found MSI capability
[    9.713046] Allocate Port Service[0000:00:1c.2:pcie00]
[    9.713086] Allocate Port Service[0000:00:1c.2:pcie02]
[    9.713189] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[    9.713244] assign_interrupt_mode Found MSI capability
[    9.713289] Allocate Port Service[0000:00:1c.3:pcie00]
[    9.713321] Allocate Port Service[0000:00:1c.3:pcie02]
[    9.713580] isapnp: Scanning for PnP cards...
[   10.067874] isapnp: No Plug & Play device found
[   10.091769] Real Time Clock Driver v1.12ac
[   10.091911] hpet_resources: 0xfed00000 is busy
[   10.091963] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   10.093063] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   10.093126] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   10.093220] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   10.096098] serio: i8042 KBD port at 0x60,0x64 irq 1
[   10.096102] serio: i8042 AUX port at 0x60,0x64 irq 12
[   11.956237] mice: PS/2 mouse device common for all mice
[   11.956345] EISA: Probing bus 0 at eisa.0
[   11.956409] EISA: Mainboard K__FFFF detected.
[   11.956444] Cannot allocate resource for EISA slot 1
[   11.956473] EISA: Detected 0 cards.
[   11.956476] cpuidle: using governor ladder
[   11.956477] cpuidle: using governor menu
[   11.956543] NET: Registered protocol family 1
[   11.956568] Using IPI No-Shortcut mode
[   11.956594] registered taskstats version 1
[   11.956697]   Magic number: 12:988:594
[   11.956752] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   11.956754] EDD information not available.
[   11.956906] Freeing unused kernel memory: 368k freed
[   10.121789] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   11.304000] fuse init (API version 7.9)
[   11.322637] ACPI: SSDT 7FEDA938, 0244 (r1  PmRef  Cpu0Ist     3000 INTL 20050624)
[   11.322795] ACPI: SSDT 7FEDA6ED, 01C6 (r1  PmRef  Cpu0Cst     3001 INTL 20050624)
[   11.323290] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[   11.323295] ACPI: Processor [CPU0] (supports 8 throttling states)
[   11.323475] ACPI: SSDT 7FEDAB7C, 00C4 (r1  PmRef  Cpu1Ist     3000 INTL 20050624)
[   11.323621] ACPI: SSDT 7FEDA8B3, 0085 (r1  PmRef  Cpu1Cst     3000 INTL 20050624)
[   13.161260] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[   13.161265] ACPI: Processor [CPU1] (supports 8 throttling states)
[   13.164981] ACPI: Thermal Zone [THM] (70 C)
[   13.450768] tg3.c:v3.86 (November 9, 2007)
[   13.450836] ACPI: PCI Interrupt 0000:09:00.0[A] -> GSI 18 (level, low) -> IRQ 18
[   13.450847] PCI: Setting latency timer of device 0000:09:00.0 to 64
[   13.466481] usbcore: registered new interface driver usbfs
[   13.466499] usbcore: registered new interface driver hub
[   13.466523] usbcore: registered new device driver usb
[   13.467440] USB Universal Host Controller Interface driver v3.0
[   13.480002] eth0: Tigon3 [partno(BCM5752KFBG) rev 6002 PHY(5752)] (PCI Express) 10/100/1000Base-T Ethernet 00:15:c5:4a:67:e0
[   13.480008] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] WireSpeed[1] TSOcap[1]
[   13.480010] eth0: dma_rwctrl[76180000] dma_mask[64-bit]
[   13.480223] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 20 (level, low) -> IRQ 20
[   13.480233] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   13.480237] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   13.480448] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   13.480479] uhci_hcd 0000:00:1d.0: irq 20, io base 0x0000bf80
[   13.480587] usb usb1: configuration #1 chosen from 1 choice
[   13.480609] hub 1-0:1.0: USB hub found
[   13.480614] hub 1-0:1.0: 2 ports detected
[   13.582986] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 21 (level, low) -> IRQ 21
[   13.582997] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   13.583001] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   13.583021] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   13.583052] uhci_hcd 0000:00:1d.1: irq 21, io base 0x0000bf60
[   13.583153] usb usb2: configuration #1 chosen from 1 choice
[   13.583173] hub 2-0:1.0: USB hub found
[   13.583177] hub 2-0:1.0: 2 ports detected
[   11.753271] SCSI subsystem initialized
[   11.792473] libata version 3.00 loaded.
[   11.849794] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 22 (level, low) -> IRQ 22
[   11.849805] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   11.849809] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   11.849829] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   11.849861] uhci_hcd 0000:00:1d.2: irq 22, io base 0x0000bf40
[   11.849960] usb usb3: configuration #1 chosen from 1 choice
[   11.849981] hub 3-0:1.0: USB hub found
[   11.849985] hub 3-0:1.0: 2 ports detected
[   13.789694] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 23 (level, low) -> IRQ 23
[   13.789703] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[   13.789707] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[   13.789726] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[   13.789756] uhci_hcd 0000:00:1d.3: irq 23, io base 0x0000bf20
[   13.789858] usb usb4: configuration #1 chosen from 1 choice
[   13.789879] hub 4-0:1.0: USB hub found
[   13.789883] hub 4-0:1.0: 2 ports detected
[   13.822559] usb 1-1: new full speed USB device using uhci_hcd and address 2
[   12.057535] ACPI: PCI Interrupt 0000:03:01.0[A] -> GSI 19 (level, low) -> IRQ 19
[   13.894651] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 20 (level, low) -> IRQ 20
[   13.894660] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   13.894664] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   13.894686] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[   13.898584] ehci_hcd 0000:00:1d.7: debug port 1
[   13.898590] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[   13.898595] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xffa80000
[   12.110240] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[19]  MMIO=[ecbff800-ecbfffff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[   13.962364] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   13.962466] usb usb5: configuration #1 chosen from 1 choice
[   13.962488] hub 5-0:1.0: USB hub found
[   13.962494] hub 5-0:1.0: 8 ports detected
[   13.982767] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 17 (level, low) -> IRQ 17
[   13.982801] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   13.982813] ACPI: PCI interrupt for device 0000:00:1f.2 disabled
[   13.990489] ata_piix 0000:00:1f.2: version 2.12
[   13.990495] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
[   13.990511] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 17 (level, low) -> IRQ 17
[   13.990533] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   13.990971] scsi0 : ata_piix
[   13.991135] scsi1 : ata_piix
[   13.991802] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xbfa0 irq 14
[   13.991805] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xbfa8 irq 15
[   12.162473] Clocksource tsc unstable (delta = -157867716 ns)
[   12.166676] ata1.00: failed to set max address (err_mask=0x1)
[   12.166682] ata1.00: device aborted resize (192426570 -> 195371568), skipping HPA handling
[   12.166693] ata1.00: ATA-7: Hitachi HTS721010G9SA00, MCZOC10H, max UDMA/100
[   12.166699] ata1.00: 192426570 sectors, multi 8: LBA48 NCQ (depth 0/32)
[   12.167705] ata1.00: configured for UDMA/100
[   12.173537] usb 1-1: device not accepting address 2, error -71
[   14.020049] ata2.00: ATAPI: PHILIPS DVD+/-RW SDVD8820, AD15, max UDMA/33
[   14.027058] ata2.00: configured for UDMA/33
[   12.190167] scsi 0:0:0:0: Direct-Access     ATA      Hitachi HTS72101 MCZO PQ: 0 ANSI: 5
[   12.191338] scsi 1:0:0:0: CD-ROM            PHILIPS  DVD+-RW SDVD8820 AD15 PQ: 0 ANSI: 5
[   12.198743] Driver 'sd' needs updating - please use bus_type methods
[   12.198800] sd 0:0:0:0: [sda] 192426570 512-byte hardware sectors (98522 MB)
[   12.198810] sd 0:0:0:0: [sda] Write Protect is off
[   12.198812] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   12.198826] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   12.198869] sd 0:0:0:0: [sda] 192426570 512-byte hardware sectors (98522 MB)
[   12.198878] sd 0:0:0:0: [sda] Write Protect is off
[   12.198879] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   12.198893] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   12.198896]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[   12.220810]  sda1 sda2 < sda5 sda6 sda7 >
[   12.258031] sd 0:0:0:0: [sda] Attached SCSI disk
[   12.261753] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   12.261769] sr 1:0:0:0: Attached scsi generic sg1 type 5
[   14.114468] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[   14.114471] Uniform CD-ROM driver Revision: 3.20
[   14.114508] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   12.468589] Attempting manual resume
[   12.468592] swsusp: Resume From Partition 8:7
[   12.468594] PM: Checking swsusp image.
[   12.468788] PM: Resume from disk failed.
[   14.342270] kjournald starting.  Commit interval 5 seconds
[   12.505245] EXT3-fs: mounted filesystem with ordered data mode.
[   12.531114] usb 5-5: new high speed USB device using ehci_hcd and address 3
[   14.437386] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[434fc00003e13c50]
[   12.663922] usb 5-5: configuration #1 chosen from 1 choice
[   13.077907] usb 1-1: new full speed USB device using uhci_hcd and address 4
[   13.220704] usb 1-1: configuration #1 chosen from 1 choice
[   13.222642] hub 1-1:1.0: USB hub found
[   13.224635] hub 1-1:1.0: 4 ports detected
[   15.403428] usb 4-1: new low speed USB device using uhci_hcd and address 2
[   13.730285] usb 4-1: configuration #1 chosen from 1 choice
[   15.787323] usb 1-1.2: new full speed USB device using uhci_hcd and address 5
[   14.077419] usb 1-1.2: configuration #1 chosen from 1 choice
[   14.079330] hub 1-1.2:1.0: USB hub found
[   14.081308] hub 1-1.2:1.0: 3 ports detected
[   14.405438] usb 1-1.4: new full speed USB device using uhci_hcd and address 6
[   14.548453] usb 1-1.4: configuration #1 chosen from 1 choice
[   14.753561] usb 1-1.2.2: new full speed USB device using uhci_hcd and address 7
[   14.870253] usb 1-1.2.2: configuration #1 chosen from 1 choice
[   20.097699] ip_tables: (C) 2000-2006 Netfilter Core Team
[   20.156352] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
[   23.309674] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   23.352969] Linux agpgart interface v0.102
[   23.469464] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   23.475285] ACPI: AC Adapter [AC] (on-line)
[   21.723341] ACPI: Battery Slot [BAT0] (battery present)
[   23.695406] input: Lid Switch as /devices/virtual/input/input2
[   23.695894] ACPI: Lid Switch [LID]
[   23.695938] input: Power Button (CM) as /devices/virtual/input/input3
[   23.721047] ACPI: Power Button (CM) [PBTN]
[   23.721102] input: Sleep Button (CM) as /devices/virtual/input/input4
[   23.752988] ACPI: Sleep Button (CM) [SBTN]
[   21.939007] ACPI: WMI-Acer: Mapper loaded
[   22.202843] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:2b/LNXVIDEO:00/input/input5
[   22.226506] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[   22.366481] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 21 (level, low) -> IRQ 21
[   22.366500] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   24.225222] nvidia: module license 'NVIDIA' taints kernel.
[   22.663244] Bluetooth: Core ver 2.11
[   22.685786] NET: Registered protocol family 31
[   22.685789] Bluetooth: HCI device and connection manager initialized
[   22.685792] Bluetooth: HCI socket layer initialized
[   22.737844] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.0
[   22.737848] iwl3945: Copyright(c) 2003-2007 Intel Corporation
[   22.737994] ACPI: PCI Interrupt 0000:0c:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[   22.738011] PCI: Setting latency timer of device 0000:0c:00.0 to 64
[   22.738031] iwl3945: Detected Intel PRO/Wireless 3945ABG Network Connection
[   22.829762] usbcore: registered new interface driver hiddev
[   22.842044] input: PS/2+USB Mouse as /devices/pci0000:00/0000:00:1d.3/usb4/4-1/4-1:1.0/input/input6
[   22.850743] Bluetooth: HCI USB driver ver 2.9
[   22.861664] input,hidraw0: USB HID v1.11 Mouse [PS/2+USB Mouse] on usb-0000:00:1d.3-1
[   22.861681] usbcore: registered new interface driver usbhid
[   22.861684] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   22.863377] usbcore: registered new interface driver hci_usb
[   23.009179] iTCO_vendor_support: vendor-support=0
[   23.081369] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[   23.081481] iTCO_wdt: Found a ICH7-M TCO device (Version=2, TCOBASE=0x1060)
[   23.081528] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   23.212603] intel_rng: FWH not detected
[   23.254475] sdhci: Secure Digital Host Controller Interface driver
[   23.254478] sdhci: Copyright(c) Pierre Ossman
[   23.294901] input: PC Speaker as /devices/platform/pcspkr/input/input7
[   23.372929] usbcore: registered new interface driver libusual
[   23.448854] Initializing USB Mass Storage driver...
[   23.471183] scsi2 : SCSI emulation for USB Mass Storage devices
[   23.479485] usbcore: registered new interface driver usb-storage
[   23.479488] USB Mass Storage support registered.
[   23.479576] usb-storage: device found at 3
[   23.479578] usb-storage: waiting for device to settle before scanning
[   25.684450] Synaptics Touchpad, model: 1, fw: 6.2, id: 0xfa0b1, caps: 0xa04713/0x200000
[   23.883276] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input8
[   25.755998] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   25.927205] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   25.927216] PCI: Setting latency timer of device 0000:01:00.0 to 64
[   25.927337] NVRM: loading NVIDIA UNIX x86 Kernel Module  169.12  Thu Feb 14 17:53:07 PST 2008
[   24.152869] sdhci: SDHCI controller found at 0000:03:01.1 [1180:0822] (rev 19)
[   24.152890] ACPI: PCI Interrupt 0000:03:01.1[B] -> GSI 18 (level, low) -> IRQ 18
[   24.152958] mmc0: SDHCI at 0xecbff500 irq 18 DMA
[   24.203637] iwl3945: Tunable channels: 13 802.11bg, 23 802.11a channels
[   24.216520] wmaster0: Selected rate control algorithm 'iwl-3945-rs'
[   24.442739] lp: driver loaded but no devices found
[   24.539310] Adding 4827492k swap on /dev/sda7.  Priority:-1 extents:1 across:4827492k
[   26.756484] EXT3 FS on sda6, internal journal
[   27.223841] kjournald starting.  Commit interval 5 seconds
[   25.387027] EXT3 FS on sda5, internal journal
[   25.387035] EXT3-fs: mounted filesystem with ordered data mode.
[   26.593132] ACPI: ACPI Dock Station Driver 
[   27.520796] apm: BIOS not found.
[   29.473809] ppdev: user-space parallel port driver
[   27.690981] audit(1213464952.840:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5646 profile="/usr/sbin/cupsd" namespace="default"
[   27.870369] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   27.870378] vboxdrv: Successfully done.
[   27.870439] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   27.870442] vboxdrv: Successfully loaded version 1.5.6_OSE (interface 0x00050002).
[   27.876708] usb-storage: device scan complete
[   29.714308] scsi 2:0:0:0: Direct-Access     SEAGATE  ST3500830A       3.AA PQ: 0 ANSI: 2
[   29.715892] sd 2:0:0:0: [sdb] 976773168 512-byte hardware sectors (500108 MB)
[   29.716766] sd 2:0:0:0: [sdb] Write Protect is off
[   29.716773] sd 2:0:0:0: [sdb] Mode Sense: 53 00 00 08
[   29.716777] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[   29.717890] sd 2:0:0:0: [sdb] 976773168 512-byte hardware sectors (500108 MB)
[   29.718762] sd 2:0:0:0: [sdb] Write Protect is off
[   29.718768] sd 2:0:0:0: [sdb] Mode Sense: 53 00 00 08
[   29.718772] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[   29.718777]  sdb: sdb1
[   29.734726] sd 2:0:0:0: [sdb] Attached SCSI disk
[   29.734792] sd 2:0:0:0: Attached scsi generic sg2 type 0
[   31.922631] Bluetooth: L2CAP ver 2.9
[   31.922636] Bluetooth: L2CAP socket layer initialized
[   32.105869] Bluetooth: RFCOMM socket layer initialized
[   32.105887] Bluetooth: RFCOMM TTY layer initialized
[   32.105890] Bluetooth: RFCOMM ver 1.8
[   42.449425] NET: Registered protocol family 10
[   42.449921] lo: Disabled Privacy Extensions
[   42.450754] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   42.451669] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   52.942067] CPU0 attaching NULL sched-domain.
[   52.942075] CPU1 attaching NULL sched-domain.
[   52.973318] CPU0 attaching sched-domain:
[   52.973322]  domain 0: span 03
[   52.973324]   groups: 01 02
[   52.973327] CPU1 attaching sched-domain:
[   52.973328]  domain 0: span 03
[   52.973329]   groups: 02 01
[   55.356902] NET: Registered protocol family 17
[   59.976004] wlan0: Initial auth_alg=0
[   59.976009] wlan0: authenticate with AP 00:90:d0:fd:45:81
[   59.977430] wlan0: RX authentication from 00:90:d0:fd:45:81 (alg=0 transaction=2 status=0)
[   59.977433] wlan0: authenticated
[   59.977435] wlan0: associate with AP 00:90:d0:fd:45:81
[   59.980203] wlan0: RX AssocResp from 00:90:d0:fd:45:81 (capab=0x411 status=0 aid=1)
[   59.980207] wlan0: associated
[   59.980255] wlan0: WMM queue=2 aci=0 acm=0 aifs=3 cWmin=15 cWmax=1023 burst=0
[   59.980258] wlan0: WMM queue=3 aci=1 acm=0 aifs=7 cWmin=15 cWmax=1023 burst=0
[   59.980260] wlan0: WMM queue=1 aci=2 acm=0 aifs=2 cWmin=7 cWmax=15 burst=30
[   59.980263] wlan0: WMM queue=0 aci=3 acm=0 aifs=2 cWmin=3 cWmax=7 burst=15
[   59.982010] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   62.170470] Inbound IN=wlan0 OUT= MAC=00:18:de:22:b3:ae:00:14:7f:fd:45:81:08:00 SRC=91.152.213.73 DST=192.168.1.64 LEN=1500 TOS=0x00 PREC=0x00 TTL=117 ID=53808 DF PROTO=TCP SPT=3724 DPT=44846 WINDOW=65535 RES=0x00 ACK URGP=0 
[   62.930249] wlan0: no IPv6 routers present

```

---

### Post by ukripper on 2008-06-14
how is transfer rate now?

---

### Post by vhadiant on 2008-06-14
Same ... good for reading, really slow for writing.

---

### Post by ukripper on 2008-06-15
> **vhadiant said:**
> Same ... good for reading, really slow for writing.

I have same controller in my dell vostro and i have just checked transfer rates and it looks fine to me and quiet quick.

I think it is boiling down to your drive itself when attached in ubuntu. can you try some other usb stick or drive and test the transfer rates?

---

### Post by zgornel on 2008-06-15
Check that your drive in not mounted in 'synchronous mode'. In KDE you can disable through the context menu for the USB Drive (Properties/Mounting).

---

### Post by vhadiant on 2008-06-15
And how would I do this in Gnome?

---

### Post by ukripper on 2008-06-15
> **vhadiant said:**
> And how would I do this in Gnome?

right click on the usb drive icon on the desktop
select "Preferences"
select the "Mounting" tab
 and uncheck Synchronous

---

### Post by vhadiant on 2008-06-15
Hmm there is no "Preferences" there. Only "Properties" and no "Mounting" tab.

---

### Post by ukripper on 2008-06-16
looks like since fesity things have changed in ubuntu in regards to that.

can do the following and then try transfering something and lets see if modprobing ehci_hcd helps your drive to boost transfer rates 
just do this in terminal:

```
sudo modprobe ehci_hcd 
```
and now test transfer rate.

and also can you post output of the following commands:
```
lsmod | grep usb
```
and 
```
uname -a
```

i think we are getting close to resolve it now.

---

### Post by dwanders on 2009-06-23
Did you guys ever come to a resolution? I have Lacie drive and it is dog slow in Ubuntu 9.04 but I am pretty sure I am using USB 2.0 (I will use this post to determine that) - but what was your resolution?:-?

---

### Post by LeonardoDaInvinci on 2009-11-20
I recently switched to Ubuntu 9.10, its my first trial with Ubuntu. Everything was fine and excited working with it, until I had to copy stuff from my 1TB external usb hard disk. It took 45 minutes to copy 1.8GB. I have USB2.0. Couldn't Imagine.
But, whatever, I am hoping and there is no dearth of developers to fix this. I am waiting. I will stick to Linux.

---

### Post by zevans on 2011-08-14
I'm in kubuntu (Maverick) and I don't have "the USB device" on my desktop, so I can't right-click on anything to change the properties...

This article 
[http://superuser.com/questions/203538/how-do-i-get-better-usb-transfer-speeds-in-xubuntu](http://superuser.com/questions/203538/how-do-i-get-better-usb-transfer-speeds-in-xubuntu)
suggests using "media:/" but I get unknown protocol when I try that.

I have remounted using -o async for now, but what a pain... where can I change the default?

---

