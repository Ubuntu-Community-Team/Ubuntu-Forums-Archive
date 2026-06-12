---
title: "No wireless detected - HP Pavilion Slimline"
date: 2008-05-31
forum: New to Ubuntu
---

### Post by hworcester on 2008-05-31
I'm trying to give new life to a (formerly) vista-clogged HP Pavilion Slimline s7713wPC. I think because of its small size, the wireless card is built in. I installed 8.04 and the wired connection is fine, but my wireless network is not detected. Here's the extent of what I get from **sudo lshw -C network**

       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:1a:73:1b:1d:e2
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

Thoughts, anyone?

---

### Post by inportb on 2008-05-31
What's the wireless chipset? You can use *lspci* to determine what you've got.

---

### Post by quelx on 2008-05-31
Probably a **Broadcom** chip since the MAC address says it's made by Gemtek Technology Co., Ltd.

verify with **lspci** as *inportb* suggested 

if so

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/)

---

### Post by hworcester on 2008-05-31
Here's the data from lspci:

00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:04.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:05.0 VGA compatible controller: nVidia Corporation C51 [GeForce 6150 LE] (rev a2)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.2 RAM memory: nVidia Corporation MCP51 Memory Controller 0 (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev a1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
02:05.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 70)
02:09.0 Communication controller: Conexant HSF 56k Data/Fax Modem

---

### Post by quelx on 2008-05-31
how about ```
lsusb -v
``` look through the output if you see something that looks wirelessy and paste the output here

---

### Post by hworcester on 2008-05-31
This is all I can see:

  iManufacturer           1 Gemtek
  iProduct                2 USB Wireless 802.11b/g adaptor
  iSerial                 0 

If a non-techie like me makes a switch to linux, MS should really start to worry.:)

---

### Post by quelx on 2008-05-31
can you post all of the **lsusb -v** output down to the **  Configuration Descriptor:** line?

for example...

```
Bus 001 Device 005: ID 123c:4567 PackardBell Computer Inc. Wireless Bluetooth
Device Descriptor:
  bLength                18
  ...
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
```

---

### Post by ugm6hr on 2008-05-31
> **hworcester said:**
> This is all I can see:

  iManufacturer           1 Gemtek
  iProduct                2 USB Wireless 802.11b/g adaptor
  iSerial                 0 

If a non-techie like me makes a switch to linux, MS should really start to worry.:)

A quick google suggests that this is a Ralink (RT) USB device, although the USB ID number should be checked (lsusb -vv)

I thought Hardy now supported them out-of-the-box?

---

### Post by quelx on 2008-05-31
Looking back over the post it looks like the device is detected (**wlan0**) so it must/might/may/mmmm be the rt73.

what does ```
lsmod|grep rt73
``` spit out?  If it indeed shows **rt73usb** then...

[http://ubuntuforums.org/showthread.php?p=4732883](http://ubuntuforums.org/showthread.php?p=4732883)

---

### Post by ugm6hr on 2008-05-31
> **quelx said:**
> what does ```
lsmod|grep rt73
``` spit out?  If it indeed shows **rt73usb** then...

[http://ubuntuforums.org/showthread.php?p=4732883](http://ubuntuforums.org/showthread.php?p=4732883)

But as I thought (from your link):
> Notice: As of Ubuntu 8.04, Most (If not all) RT73 based devices are supported out-of-the-box.

Hmmm....

---

### Post by quelx on 2008-05-31
> **ugm6hr said:**
> A quick google suggests that this is a Ralink (RT) USB device, although the USB ID number should be checked (lsusb -vv)

I thought Hardy now supported them out-of-the-box?

Well it *could* be a rt2500

in which case **ndiswrapper** is apparently still needed.

[http://ubuntuforums.org/showpost.php?p=3450169&postcount=1](http://ubuntuforums.org/showpost.php?p=3450169&postcount=1)

**lsmod** should give us a hint, I suspect you are right and it is handled by **rt73usb** module and just needs a network setup.

---

### Post by heinig on 2008-05-31
I have a HP Slimline s7600e and got my wireless working out of the box since Gutsy.  Right now it's using the rt73usb driver without any problem, but I'm not sure if the device is a RT2500 or something else.

---

### Post by hworcester on 2008-06-01
Originally Posted by quelx  View Post
[I]what does
Code:

lsmod|grep rt73

spit out? If it indeed shows rt73usb then...

[http://ubuntuforums.org/showthread.php?p=4732883](http://ubuntuforums.org/showthread.php?p=4732883)[/I]

Yes, I did see something about rt73usb and ran the RT73 Wireless Device Installer Script posted in the thread, but now I don't even see "wireless" as an option in the network manager. It appears to have vanished. Thoughts?

---

### Post by ugm6hr on 2008-06-01
> **hworcester said:**
> Yes, I did see something about rt73usb and ran the RT73 Wireless Device Installer Script posted in the thread, but now I don't even see "wireless" as an option in the network manager. It appears to have vanished. Thoughts?

As that thread / script states - this chipset is now supported without any modification in Hardy.

That script was for Gutsy.

What version of Ubuntu are you using?

I'm afraid I don't know what that script has done; if anyone does - you are best trying to reverse it (or just reinstall).

Do you have a BIOS switch or hardware switch for wifi / LAN?  Is the LED on for the device (if you have one)?

Also - look here: [http://ubuntuforums.org/showthread.php?p=5024425](http://ubuntuforums.org/showthread.php?p=5024425) (see point 8 ) - this is for XP, but I have no doubt Vista does something similar.

If / when you get back to the starting point, repost the full lshw -C network.

---

### Post by hworcester on 2008-06-04
OK, back to square one. I just reinstalled version 8.04. My computer is an HP Pav. Slimline 7713 with built-in wireless card. Here's all I get with the command you recommended:

henry@henry-desktop:~$ sudo lshw -C network
[sudo] password for henry: 
  *-network               
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:1a:73:1b:1d:e2
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

---

