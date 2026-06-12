---
title: "[SOLVED] Problems using Suspend, can't find appropriate forum, test"
date: 2008-08-05
forum: New to Ubuntu
---

### Post by njd4k on 2008-08-05
I've been having problems using Suspend on my laptop -- sometimes it seems to work just fine, but sometimes it locks up at the password screen to get back in. Even when it appears to work fine a box informs me that my computer didn't suspend properly. So I looked at the help files and it said to come to the forums and look into running some tests to identify the problem.

I found the Dell testing pages, but nobody has posted anything for my model since Feisty.

[https://wiki.ubuntu.com/LaptopTestingTeam/DellInspironE1505](https://wiki.ubuntu.com/LaptopTestingTeam/DellInspironE1505)

Does anybody know the problem with Hardy? I should probably fill out a laptop testing report, but I'm such a novice I'm not sure I wouldn't file it incompletely and do more harm than good.

---

### Post by phidia on 2008-08-05
When it locks up do you need to do a hard reboot? You can look at the system logfiles. There is a gui method to do this in hardy from the top panel menu System > Administration (I'm not in a hardy install) but it's called system logs or something like that. The other, slightly more complicated way, is just to open Places > system > /var/log/ and look at dmesg or messages.
You can post any messages that look related to the lock up.

---

### Post by njd4k on 2008-08-05
Thank you for pointing me in this direction. After the most recent occurrence I found the messages log. Nothing actually looks to this noob like the explanation; the biggest error I can find is

```
Aug  5 21:50:26 nic-laptop kernel: [    0.433781] ata2.00: _GTF evaluation failed (AE 0x1001)
```

What does that mean? Is that the problem?

From the GUI, the password box to log back in pops up with a blinking cursor, but the mouse and keyboard don't respond to inputs. The computer just freezes there (or the trackpad and keyboard do, anyway).

Here's the complete message log, starting with the suspend and ending with the hard restart.

```
Aug  5 19:41:41 nic-laptop kernel: [ 8069.436498] ACPI: PCI interrupt for device 0000:03:00.0 disabled
Aug  5 19:41:42 nic-laptop kernel: [ 8069.521567] ACPI: PCI interrupt for device 0000:0b:00.0 disabled
Aug  5 19:41:44 nic-laptop kernel: [ 8071.944791] Syncing filesystems ... done.
Aug  5 21:50:26 nic-laptop kernel: [ 8071.945088] Freezing user space processes ... (elapsed 0.00 seconds) done.
Aug  5 21:50:26 nic-laptop kernel: [ 8071.945764] Freezing remaining freezable tasks ... (elapsed 0.09 seconds) done.
Aug  5 21:50:26 nic-laptop kernel: [ 8072.043578] Suspending console(s)
Aug  5 21:50:26 nic-laptop kernel: [ 8072.043629] sd 0:0:0:0: [sda] Synchronizing SCSI cache
Aug  5 21:50:26 nic-laptop kernel: [ 8072.043821] sd 0:0:0:0: [sda] Stopping disk
Aug  5 21:50:26 nic-laptop kernel: [ 8072.052666] ACPI: PCI interrupt for device 0000:03:01.1 disabled
Aug  5 21:50:26 nic-laptop kernel: [ 8072.058245] [fglrx] firegl_gps_setpowerdown .
Aug  5 21:50:26 nic-laptop kernel: [ 8073.915641] ACPI: PCI interrupt for device 0000:01:00.0 disabled
Aug  5 21:50:26 nic-laptop kernel: [ 8073.915808] ACPI: PCI interrupt for device 0000:00:1f.2 disabled
Aug  5 21:50:26 nic-laptop kernel: [ 8073.916093] ACPI: PCI interrupt for device 0000:00:1d.7 disabled
Aug  5 21:50:26 nic-laptop kernel: [ 8073.916228] ACPI: PCI interrupt for device 0000:00:1d.3 disabled
Aug  5 21:50:26 nic-laptop kernel: [ 8073.916264] ACPI: PCI interrupt for device 0000:00:1d.2 disabled
Aug  5 21:50:26 nic-laptop kernel: [ 8073.916300] ACPI: PCI interrupt for device 0000:00:1d.1 disabled
Aug  5 21:50:26 nic-laptop kernel: [ 8073.916335] ACPI: PCI interrupt for device 0000:00:1d.0 disabled
Aug  5 21:50:26 nic-laptop kernel: [ 8073.916708] ACPI: PCI interrupt for device 0000:00:1b.0 disabled
Aug  5 21:50:26 nic-laptop kernel: [ 8073.920712] Disabling non-boot CPUs ...
Aug  5 21:50:26 nic-laptop kernel: [ 8074.032602] CPU 1 is now offline
Aug  5 21:50:26 nic-laptop kernel: [ 8074.032605] SMP alternatives: switching to UP code
Aug  5 21:50:26 nic-laptop kernel: [ 8074.034172] CPU1 is down
Aug  5 21:50:26 nic-laptop kernel: [    0.280961] Enabling non-boot CPUs ...
Aug  5 21:50:26 nic-laptop kernel: [    0.291166] SMP alternatives: switching to SMP code
Aug  5 21:50:26 nic-laptop kernel: [    0.292278] Booting processor 1/2 APIC 0x1
Aug  5 21:50:26 nic-laptop kernel: [    0.302535] Initializing CPU#1
Aug  5 21:50:26 nic-laptop kernel: [    0.382918] Calibrating delay using timer specific routine.. 3657.39 BogoMIPS (lpj=7314792)
Aug  5 21:50:26 nic-laptop kernel: [    0.382925] CPU: L1 I cache: 32K, L1 D cache: 32K
Aug  5 21:50:26 nic-laptop kernel: [    0.382927] CPU: L2 cache: 2048K
Aug  5 21:50:26 nic-laptop kernel: [    0.382929] CPU 1/1 -> Node 0
Aug  5 21:50:26 nic-laptop kernel: [    0.382931] CPU: Physical Processor ID: 0
Aug  5 21:50:26 nic-laptop kernel: [    0.382932] CPU: Processor Core ID: 1
Aug  5 21:50:26 nic-laptop kernel: [    0.383267] Intel(R) Core(TM)2 CPU         T5600  @ 1.83GHz stepping 06
Aug  5 21:50:26 nic-laptop kernel: [    0.383813] CPU1 is up
Aug  5 21:50:26 nic-laptop kernel: [    0.430965] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 21 (level, low) -> IRQ 21
Aug  5 21:50:26 nic-laptop kernel: [    0.431242] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 20 (level, low) -> IRQ 20
Aug  5 21:50:26 nic-laptop kernel: [    0.431313] usb usb1: root hub lost power or was reset
Aug  5 21:50:26 nic-laptop kernel: [    0.431337] PCI: Enabling device 0000:00:1d.1 (0000 -> 0001)
Aug  5 21:50:26 nic-laptop kernel: [    0.431341] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 21 (level, low) -> IRQ 21
Aug  5 21:50:26 nic-laptop kernel: [    0.431420] usb usb2: root hub lost power or was reset
Aug  5 21:50:26 nic-laptop kernel: [    0.431442] PCI: Enabling device 0000:00:1d.2 (0000 -> 0001)
Aug  5 21:50:26 nic-laptop kernel: [    0.431447] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 22 (level, low) -> IRQ 22
Aug  5 21:50:26 nic-laptop kernel: [    0.431526] usb usb3: root hub lost power or was reset
Aug  5 21:50:26 nic-laptop kernel: [    0.431548] PCI: Enabling device 0000:00:1d.3 (0000 -> 0001)
Aug  5 21:50:26 nic-laptop kernel: [    0.431552] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 23 (level, low) -> IRQ 23
Aug  5 21:50:26 nic-laptop kernel: [    0.431630] usb usb4: root hub lost power or was reset
Aug  5 21:50:26 nic-laptop kernel: [    0.431769] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 20 (level, low) -> IRQ 20
Aug  5 21:50:26 nic-laptop kernel: [    0.432136] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 17 (level, low) -> IRQ 17
Aug  5 21:50:26 nic-laptop kernel: [    0.433781] ata2.00: _GTF evaluation failed (AE 0x1001)
Aug  5 21:50:26 nic-laptop kernel: [    0.434044] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
Aug  5 21:50:26 nic-laptop kernel: [    0.436458] [fglrx] firegl_gps_setpowerup .
Aug  5 21:50:26 nic-laptop gnome-power-manager: (nic) Resuming computer
Aug  5 21:50:26 nic-laptop kernel: [    0.847336] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[19]  MMIO=[ef9fd800-ef9fdfff]  Max Packet=[2048]  IR/IT contexts=[4/4]
Aug  5 21:50:26 nic-laptop kernel: [    0.853598] ACPI: PCI Interrupt 0000:03:01.1[B] -> GSI 18 (level, low) -> IRQ 18
Aug  5 21:50:26 nic-laptop kernel: [    1.132161] ata2.00: configured for UDMA/33
Aug  5 21:50:26 nic-laptop kernel: [    1.394170] ata1.00: configured for UDMA/100
Aug  5 21:50:26 nic-laptop kernel: [    1.394215] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
Aug  5 21:50:26 nic-laptop kernel: [    1.394235] sd 0:0:0:0: [sda] Write Protect is off
Aug  5 21:50:26 nic-laptop kernel: [    1.394267] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Aug  5 21:50:26 nic-laptop kernel: [    1.443749] sd 0:0:0:0: [sda] Starting disk
Aug  5 21:50:26 nic-laptop kernel: [    1.444422] Restarting tasks ... done.
Aug  5 21:50:28 nic-laptop kernel: [    2.686250] ACPI: PCI Interrupt 0000:0b:00.0[A] -> GSI 16 (level, low) -> IRQ 16
Aug  5 21:50:28 nic-laptop kernel: [    2.696340] ssb: Core 0 found: ChipCommon (cc 0x800, rev 0x11, vendor 0x4243)
Aug  5 21:50:28 nic-laptop kernel: [    2.696383] ssb: Core 1 found: IEEE 802.11 (cc 0x812, rev 0x0A, vendor 0x4243)
Aug  5 21:50:28 nic-laptop kernel: [    2.696408] ssb: Core 2 found: USB 1.1 Host (cc 0x817, rev 0x03, vendor 0x4243)
Aug  5 21:50:28 nic-laptop kernel: [    2.696434] ssb: Core 3 found: PCI-E (cc 0x820, rev 0x01, vendor 0x4243)
Aug  5 21:50:28 nic-laptop kernel: [    2.700337] ssb: Sonics Silicon Backplane found on PCI device 0000:0b:00.0
Aug  5 21:50:28 nic-laptop kernel: [    2.706056] b43-phy0: Broadcom 4311 WLAN found
Aug  5 21:50:28 nic-laptop kernel: [    2.797810] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 17 (level, low) -> IRQ 17
Aug  5 21:50:28 nic-laptop kernel: [    2.817860] ssb: Core 0 found: Fast Ethernet (cc 0x806, rev 0x07, vendor 0x4243)
Aug  5 21:50:28 nic-laptop kernel: [    2.817878] ssb: Core 1 found: V90 (cc 0x807, rev 0x03, vendor 0x4243)
Aug  5 21:50:28 nic-laptop kernel: [    2.817888] ssb: Core 2 found: PCI (cc 0x804, rev 0x0A, vendor 0x4243)
Aug  5 21:50:28 nic-laptop kernel: [    2.836725] input: b43-phy0 as /devices/virtual/input/input13
Aug  5 21:50:28 nic-laptop kernel: [    2.860973] ssb: Sonics Silicon Backplane found on PCI device 0000:03:00.0
Aug  5 21:50:28 nic-laptop kernel: [    2.861021] b44.c:v2.0
Aug  5 21:50:29 nic-laptop kernel: [    4.244266] Registered led device: b43-phy0:tx
Aug  5 21:50:29 nic-laptop kernel: [    4.244313] Registered led device: b43-phy0:rx
Aug  5 21:50:29 nic-laptop kernel: [    4.244349] Registered led device: b43-phy0:radio
Aug  5 21:50:29 nic-laptop kernel: [    4.255029] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Aug  5 21:50:29 nic-laptop kernel: [    4.265508] eth0: Broadcom 44xx/47xx 10/100BaseT Ethernet 00:15:c5:d0:05:62
Aug  5 21:50:29 nic-laptop kernel: [    4.339088] ADDRCONF(NETDEV_UP): eth0: link is not ready
Aug  5 21:50:30 nic-laptop kernel: [    4.664699] ADDRCONF(NETDEV_UP): eth0: link is not ready
Aug  5 21:50:30 nic-laptop kernel: [    4.686783] input: b43-phy0 as /devices/virtual/input/input14
Aug  5 21:50:31 nic-laptop kernel: [    6.044102] Registered led device: b43-phy0:tx
Aug  5 21:50:31 nic-laptop kernel: [    6.044378] Registered led device: b43-phy0:rx
Aug  5 21:50:31 nic-laptop kernel: [    6.044597] Registered led device: b43-phy0:radio
Aug  5 21:50:31 nic-laptop kernel: [    6.064550] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Aug  5 21:50:45 nic-laptop kernel: [    6.975915] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Aug  5 21:50:57 nic-laptop gnome-power-manager: (nic) GNOME interactive logout. Reason: The power button has been pressed.
Aug  5 21:50:59 nic-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.host_name
Aug  5 21:50:59 nic-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.nis_domain
Aug  5 21:50:59 nic-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.nis_servers
Aug  5 21:50:59 nic-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.interface_mtu
Aug  5 21:51:41 nic-laptop syslogd 1.5.0#1ubuntu1: restart.
```

---

### Post by njd4k on 2008-08-06
It sounds like this would fix my problem, if I could set libdata.noacpi=1

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/202767](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/202767)

I assume this is something I could open in gedit and tweak? I have tried to find the libdata file but I'm having no luck.

---

### Post by njd4k on 2008-10-31
I never did figure out how to test my laptop, but switching to 32-bit 8.10 fixed my problem. Marking as solved.

---

