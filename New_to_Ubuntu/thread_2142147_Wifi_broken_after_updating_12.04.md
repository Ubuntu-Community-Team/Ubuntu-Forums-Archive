---
title: "Wifi broken after updating 12.04"
date: 2013-05-04
forum: New to Ubuntu
---

### Post by Zornicator on 2013-05-04
I installed 12.04 on a Thinkpad w530 with Windows 7 preinstalled.

Wifi worked perfectly until I allowed ubuntu to install upgrades and restart, after which I could not use the available Wifi networks. The one I'd been using was no longer detected, but others were detected. Wifi still works fine in the Windows partition.

I installed Wicd and purged Network Manager, as per instructions found here:

[http://www.techdrivein.com/2012/09/slow-erratic-wifi-ubuntu1204-fixed.html](http://www.techdrivein.com/2012/09/slow-erratic-wifi-ubuntu1204-fixed.html)

All networks are detected, but I cannot connect (Wicd flashes "Bad Password" after hanging on "verifying authentication" for about a minute). Wired connection is working.

This is my first post and I know nothing. Thanks for your time!

---

### Post by Zornicator on 2013-05-05
New development:

Wifi alternates between working and giving me the same "Bad Password" result. Only action I took between the above post and now was to boot in recovery mode (as suggested in a reply to another of my posts about failing to "restart"). But I didn't do anything in recovery mode, just booted into it and shutdown again.

I can't call this resolved because I have still have no idea what's going on. Ideas, anyone?

---

### Post by BluNova on 2013-05-05
Type the following commands into the terminal and post the results
```
lspci
lsusb
```

---

### Post by Zornicator on 2013-05-05
Thanks BluNova, here are the results:

for lspci:

```
[FONT=arial]00:00.0 Host bridge: Intel Corporation Ivy Bridge DRAM Controller (rev 09)[/FONT]
[FONT=arial]00:01.0 PCI bridge: Intel Corporation Ivy Bridge PCI Express Root Port (rev 09)[/FONT]
[FONT=arial]00:02.0 VGA compatible controller: Intel Corporation Ivy Bridge Graphics Controller (rev 09)[/FONT]
[FONT=arial]00:14.0 USB controller: Intel Corporation Panther Point USB xHCI Host Controller (rev 04)[/FONT]
[FONT=arial]00:16.0 Communication controller: Intel Corporation Panther Point MEI Controller #1 (rev 04)[/FONT]
[FONT=arial]00:16.3 Serial controller: Intel Corporation Panther Point KT Controller (rev 04)[/FONT]
[FONT=arial]00:19.0 Ethernet controller: Intel Corporation 82579LM Gigabit Network Connection (rev 04)[/FONT]
[FONT=arial]00:1a.0 USB controller: Intel Corporation Panther Point USB Enhanced Host Controller #2 (rev 04)[/FONT]
[FONT=arial]00:1b.0 Audio device: Intel Corporation Panther Point High Definition Audio Controller (rev 04)[/FONT]
[FONT=arial]00:1c.0 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 1 (rev c4)[/FONT]
[FONT=arial]00:1c.1 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 2 (rev c4)[/FONT]
[FONT=arial]00:1c.2 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 3 (rev c4)[/FONT]
[FONT=arial]00:1d.0 USB controller: Intel Corporation Panther Point USB Enhanced Host Controller #1 (rev 04)[/FONT]
[FONT=arial]00:1f.0 ISA bridge: Intel Corporation Panther Point LPC Controller (rev 04)[/FONT]
[FONT=arial]00:1f.2 SATA controller: Intel Corporation Panther Point 6 port SATA Controller [AHCI mode] (rev 04)[/FONT]
[FONT=arial]00:1f.3 SMBus: Intel Corporation Panther Point SMBus Controller (rev 04)[/FONT]
[FONT=arial]01:00.0 VGA compatible controller: NVIDIA Corporation Device 0ffc (rev a1)[/FONT]
[FONT=arial]02:00.0 System peripheral: Ricoh Co Ltd MMC/SD Host Controller (rev 08)[/FONT]
[FONT=arial]02:00.3 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 PCIe IEEE 1394 Controller (rev 04)[/FONT]
[FONT=arial]03:00.0 Network controller: Intel Corporation Centrino Advanced-N 6205 (rev 34)[/FONT]

```

And for lsusb:

```
[FONT=arial]Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub[/FONT]
[FONT=arial]Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub[/FONT]
[FONT=arial]Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub[/FONT]
[FONT=arial]Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub[/FONT]
[FONT=arial]Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub[/FONT]
[FONT=arial]Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub[/FONT]
[FONT=arial]Bus 001 Device 003: ID 147e:2020 Upek [/FONT]
[FONT=arial]Bus 001 Device 004: ID 04f2:b2eb Chicony Electronics Co., Ltd[/FONT]
```

---

### Post by Zornicator on 2013-05-30
Is there any way this had to do with dual booting? I have since reinstalled, giving the whole device over to Ubuntu. No problems with wireless now!

---

