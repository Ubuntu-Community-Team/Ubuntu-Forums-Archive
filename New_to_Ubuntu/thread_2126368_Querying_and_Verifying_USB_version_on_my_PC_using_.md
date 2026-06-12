---
title: "Querying and Verifying USB version on my PC using CLI Terminal"
date: 2013-03-16
forum: New to Ubuntu
---

### Post by ac5jw on 2013-03-16
I am not certain about the version of USB supported by my PC.  I have a SysInfo summary, but I do not see this specific information.  Can I query my system for this information using CLI Terminal?

I do not want to trust marketing or sales information alone.  But I want to know what my system will detect and report that is installed.  I wish to confirm that I have either USB v1.1 or USB 2.0 protocol.

I see a note on a sales document referencing USB2 in a description for MBA-K8V/DX Asus K8V-Deluxe VIA K8T800, Audio, Gig LAN, SATA, RAID, USB2, 1394, DDR400.

Any ideas ?

Thanks for reading.

:confused:

---

### Post by DuckHook on 2013-03-16
```
sudo lshw -C bus | grep -iA13 usb
```will give you a listing of your usb devices. Look for something like "USB2 Enhanced Host Controller" which will confirm that you have USB 2 capabilities.

---

### Post by Toz on 2013-03-17
Or how about **lsusb**?
```

$ lsusb
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
[COLOR="#0000FF"]Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub[/COLOR]
[COLOR="#FF0000"]Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub[/COLOR]
Bus 001 Device 003: ID 04f2:b346 Chicony Electronics Co., Ltd 
Bus 002 Device 003: ID 8087:07da Intel Corp. 

```

---

### Post by DuckHook on 2013-03-17
> **Toz said:**
> Or how about **lsusb**?

...but why do it the easy way when there's an alternative totally shrouded in obscurity? :biggrin:

---

### Post by ac5jw on 2013-03-17
Hey guys, thanks for your posts and for the commands to use.  It will be a big help.  Opening my terminal now ... :P

---

### Post by ac5jw on 2013-03-17
OK I tried the SHORT form first LOL :) and here are my results.

raleigh@ac5jw:~$ lsusb

Bus 001 Device 002: ID 1a40:0201 Terminus Technology Inc. Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 046d:c03e Logitech, Inc. Premium Optical Wheel Mouse (M-BT58)
Bus 001 Device 004: ID 046d:0819 Logitech, Inc. Webcam C210

It appears that I only have USB version 1.1 support on my PC.  I was always under the impression that it was really USB 2.0 because it was a "newer" hand-me-down PC.  But I do see some references to 2.0 in my device list.  I will explore further with the LONG command version !

---

### Post by ac5jw on 2013-03-17
OK, I did it :P Here are the results from the LONG command:

raleigh@ac5jw:~$ sudo lshw -C bus | grep -iA13 usb
[sudo] password for raleigh: 
  *-usb:0
       description: USB controller
       product: VT82xxxxx UHCI USB 1.1 Controller
       vendor: VIA Technologies, Inc.
       physical id: 10
       bus info: pci@0000:00:10.0
       version: 81
       width: 32 bits
       clock: 33MHz
       capabilities: pm uhci bus_master cap_list
       configuration: driver=uhci_hcd latency=64
       resources: irq:21 ioport:b400(size=32)
  *-usb:1
       description: USB controller
       product: VT82xxxxx UHCI USB 1.1 Controller
       vendor: VIA Technologies, Inc.
       physical id: 10.1
       bus info: pci@0000:00:10.1
       version: 81
       width: 32 bits
       clock: 33MHz
       capabilities: pm uhci bus_master cap_list
       configuration: driver=uhci_hcd latency=64
       resources: irq:21 ioport:b800(size=32)
  *-usb:2
       description: USB controller
       product: VT82xxxxx UHCI USB 1.1 Controller
       vendor: VIA Technologies, Inc.
       physical id: 10.2
       bus info: pci@0000:00:10.2
       version: 81
       width: 32 bits
       clock: 33MHz
       capabilities: pm uhci bus_master cap_list
       configuration: driver=uhci_hcd latency=64
       resources: irq:21 ioport:c000(size=32)
  *-usb:3
       description: USB controller
       product: VT82xxxxx UHCI USB 1.1 Controller
       vendor: VIA Technologies, Inc.
       physical id: 10.3
       bus info: pci@0000:00:10.3
       version: 81
       width: 32 bits
       clock: 33MHz
       capabilities: pm uhci bus_master cap_list
       configuration: driver=uhci_hcd latency=64
       resources: irq:21 ioport:c400(size=32)
  *-usb:4
       description: USB controller
       product: USB 2.0
       vendor: VIA Technologies, Inc.
       physical id: 10.4
       bus info: pci@0000:00:10.4
       version: 86
       width: 32 bits
       clock: 33MHz
       capabilities: pm ehci bus_master cap_list
       configuration: driver=ehci_hcd latency=64
       resources: irq:21 memory:fdf00000-fdf000ff
raleigh@ac5jw:~$ 

Everything looks like USB version 1.1 but I notice the last return was for USB version 2.0 in the -usb:4 category.  Can anyone tell me more about that entry?  I hope to learn enough to use the v2.0 for its higher speed if I can activate it and connect my devices through that controller.  :confused:

---

### Post by DuckHook on 2013-03-17
You have USB 2 support. Both commands show this. However, this support is restricted to only certain ports. This is also entirely expected behaviour. You should download the spec sheet of your motherboard to determine which are your USB 2.0 ports.

---

### Post by ac5jw on 2013-03-17
OK Thanks for the interpretation on my data.  I will look up some specs on my motherboard as you suggest.

Best,

Raleigh - ac5jw

---

### Post by ac5jw on 2013-03-31
Update.  I have been playing with the lspci and lsusb commands in the terminal and I also experimented with disconnecting my USB extrnal hub and its three devices.  The results of the lsusb command are the same now as they were when I first posted them here earlier in this thread.  I noticed today (finally) that the USB 2.0 controller on my PC is on Bus 001, while the other USB 1.1 controllers are isolated and confined to other Bus numbers 002 to 005.  

During my experiment today,  I tried disconnecting my external hub along with its three devices and reconnected to different ports.  Most of the time, I got results indicating I was remaining on Bus 001.  But briefly I saw my lsusb show my devices going on Bus 003.  Later rechecks showed they were back on Bus 001.

I wonder if my computer is autosensing the port connections and assigning different buses to the same port based on power and device speed?  My external USB hub is supposed to be USB 2.0 but I have a mouse, a webcam, and an audio headset adapter plugged into my hub, and I am thinking that my mouse may be v1.1 without further checking online.  So for a brief redirect to Bus 003, I am thinking that the mouse was detected first by the PC and was assigned a lower power and speed with Bus 003, which propogated to all my devices and my external hub.  In the exact same port, I was later able to get a result with all my devices and external hub back again on Bus 001.

It is a little confusing and new to me, but I am making the presumption that I have always been on USB 2.0 controller and just did not know it yet.  But with my data from today matching the data I posted previously on lsusb lookups, I am more convinced.

Thanks to everyone for your help and your time in discussing this with me and giving me ideas to try!

R

---

