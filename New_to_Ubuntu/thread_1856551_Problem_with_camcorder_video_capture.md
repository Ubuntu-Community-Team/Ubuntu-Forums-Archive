---
title: "Problem with camcorder video capture"
date: 2011-10-08
forum: New to Ubuntu
---

### Post by scubasean on 2011-10-08
I have scoured threads and tried everything to see if I can get my camcorder to download video. I think I need someone to tell me how to do this step by step.

I am using Natty studio and trying to use kino but get the 
:

WARNING: raw1394 kernal module not loaded or failure to read/write/dev/raw1394!

Error message. This, I understand, is because Natty doesn't have the raw stack installed. This is where I get confused. Some threads seem to say I don't need it  others offer options to install/use it (none of which seem to work).

Can anybody help me?

Sean

---

### Post by egalvan on 2011-10-08
> **scubasean said:**
> 

I am using Natty studio and trying to use kino but get the 
:

WARNING: raw1394 kernal module not loaded or failure to read/write/dev/raw1394!

Error message. This, I understand, is because Natty doesn't have the raw stack installed.
  others offer** options to install/use it** (none of which seem to work).

Sean

How are you trying to install 'raw1394'?

In Natty, under Synaptic, a search for 'raw1394' turns up 'libraw1394', which appears to be exactly what you need.

> library for direct access to IEEE 1394 bus (aka FireWire)

libraw1394 is the only supported interface to the kernel side raw1394
of the Linux IEEE-1394 subsystem, which provides direct access to the
connected 1394 buses to user space.  Through libraw1394/raw1394,
applications can directly send to and receive from other nodes without
requiring a kernel driver for the protocol in question.

---

### Post by stmiller on 2011-10-09
```
sudo apt-get install dvgrab
```

Then connect your camera via firewire, put in play mode, and then type:

```
dvgrab
```

---

### Post by scubasean on 2011-10-11
Thanks both of you for taking the time to reply.

Egalvan - I am afraid I already have those packages installed.

Stmiller - when I type dvgrab I get the response:

Error: no camera exists

When I check my pci devices with lspci I get:

00:00.0 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
00:00.5 PIC: VIA Technologies, Inc. CN896/VN896/P4M900 I/O APIC Interrupt Controller
00:00.6 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Security Device
00:00.7 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237/VX700 PCI Bridge
00:02.0 PCI bridge: VIA Technologies, Inc. CN896/VN896/P4M900 PCI to PCI Bridge Controller (rev 80)
00:03.0 PCI bridge: VIA Technologies, Inc. CN896/VN896/P4M900 PCI to PCI Bridge Controller (rev 80)
00:08.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev 80)
00:0f.0 IDE interface: VIA Technologies, Inc. Device 5337 (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 07)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237A PCI to ISA Bridge
00:11.7 Host bridge: VIA Technologies, Inc. VT8251 Ultra VLINK Controller
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 7c)
00:13.0 Host bridge: VIA Technologies, Inc. VT8237A Host Bridge
02:00.0 VGA compatible controller: nVidia Corporation G72 [GeForce 7300 SE/7200 GS] (rev a1)
80:01.0 Audio device: VIA Technologies, Inc. VT1708/A [Azalia HDAC] (VIA High Definition Audio Controller) (rev 10)

Indicating the card is installed. Can you suggest anything else?

Thanks again

Sean

---

### Post by scubasean on 2011-10-27
I seem to be able to access my camera through kino now. but only when kino is opened through root e.g. sudo kino.

It is intermittent and only seems to be able to capture mins at a time before crashing.

Not sure if anybody know's the solution to this?

Thanks

Sean

---

### Post by glenstewart on 2011-11-17
See comment #2 at [https://bugs.launchpad.net/ubuntu/+source/dvgrab/+bug/779680](https://bugs.launchpad.net/ubuntu/+source/dvgrab/+bug/779680)

---

