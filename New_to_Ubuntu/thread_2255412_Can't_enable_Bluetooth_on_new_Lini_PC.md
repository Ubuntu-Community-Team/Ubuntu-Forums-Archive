---
title: "Can't enable Bluetooth on new Lini PC"
date: 2014-12-04
forum: New to Ubuntu
---

### Post by James_Creasy on 2014-12-04
Just got a Lini PC to replace my Mac Mini. New to Linux, please be gentle. :)

Came with Xubuntu 14.04, could not pair my Apple wireless keyboard, I unpaired it from the Mac of course. 

Was not able to see any devices in the Settings UI, says "No Bluetooth adapters found"

I then installed the Unity desktop and Blueman, no difference, can't see any devices, including an iPad on Bluetooth.

Here's the output of lspci
```

00:00.0 Host bridge: Intel Corporation 4th Gen Core Processor DRAM Controller (rev 06)
00:02.0 VGA compatible controller: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller (rev 06)
00:03.0 Audio device: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller (rev 06)
00:14.0 USB controller: Intel Corporation Device 8cb1
00:16.0 Communication controller: Intel Corporation Device 8cba
00:19.0 Ethernet controller: Intel Corporation Ethernet Connection (2) I218-V
00:1a.0 USB controller: Intel Corporation Device 8cad
00:1b.0 Audio device: Intel Corporation Device 8ca0
00:1c.0 PCI bridge: Intel Corporation Device 8c90 (rev d0)
00:1c.3 PCI bridge: Intel Corporation Device 8c96 (rev d0)
00:1d.0 USB controller: Intel Corporation Device 8ca6
00:1f.0 ISA bridge: Intel Corporation Device 8cc4
00:1f.2 SATA controller: Intel Corporation Device 8c82
00:1f.3 SMBus: Intel Corporation Device 8ca2
02:00.0 Network controller: Broadcom Corporation BCM4352 802.11ac Wireless Network Adapter (rev 03)

```
lsusb
```

Bus 002 Device 002: ID 8087:8001 Intel Corp.
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8009 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 006: ID 05ac:020b Apple, Inc. Pro Keyboard [Mitsumi, A1048/US layout]
Bus 003 Device 003: ID 05ac:1003 Apple, Inc. Hub in Pro Keyboard [Mitsumi, A1048]
Bus 003 Device 002: ID 093a:2510 Pixart Imaging, Inc. Optical Mouse
Bus 003 Device 005: ID 059b:0370 Iomega Corp.
Bus 003 Device 004: ID 13d3:3404 IMC Networks
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```
hciconfig returns nothing.

and 
 
hcitool dev
Devices:


and

bluetoothd -d -n
```

bluetoothd[6491]: Bluetooth daemon 4.101
bluetoothd[6491]: Parsing /etc/bluetooth/main.conf failed: No such file or directory
D-Bus setup failed: Connection ":1.225" is not allowed to own the service "org.bluez" due to security policies in the configuration file
bluetoothd[6491]: Unable to get on D-Bus

```
and

start bluetooth
start: Unknown job: bluetooth
I see no Bluetooth icon in the status area.


I contacted the vendor, who insisted there is Bluetooth hardware. I just can't find it. 

I'm missing the bluetooth/main.conf file, I am expected to code that from the man page?

---

### Post by James_Creasy on 2014-12-17
Update: It might that this card does not work with Ubuntu 14.04. I upgraded to 14.10 on the advice of the hardware vendor which caused more Bluetooth options to appear in UI but still not able to pair Apple Wireless keyboard. Finally bought new keyboard which resolved the problem.

---

