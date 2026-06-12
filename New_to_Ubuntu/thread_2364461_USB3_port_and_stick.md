---
title: "USB3 port and stick"
date: 2017-06-23
forum: New to Ubuntu
---

### Post by dockson on 2017-06-23
Heya,

I am fairly new to Linux, just installed Ubuntu GNOME on my laptop and I am having a little problem with my USB stick.
The laptop is a Lenovo Ideapad Y510P, no other system is installed on it atm apart from Ubuntu GNOME 17.04.

First, this is what the output from lsusb is:
```

Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 003: ID 8087:07da Intel Corp. 
Bus 003 Device 002: ID 174f:1474 Syntek 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

I have an USB3 stick which I want to insert into one of the two USB3 ports. It gets recognized just fine:

Port 1
```

Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 003: ID 0951:1666 Kingston Technology DataTraveler G4
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 003: ID 8087:07da Intel Corp. 
Bus 003 Device 002: ID 174f:1474 Syntek 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

Port2
```

Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 011: ID 0951:1666 Kingston Technology DataTraveler G4
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 003: ID 8087:07da Intel Corp. 
Bus 003 Device 002: ID 174f:1474 Syntek 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

However, no interaction happens. I can't actually access the usb. It works just fine with the USB2 port that I have. Loads almost immediately.
The two USB3 ports also work with USB2 devices. It's just an USB3 device won't work with the USB3 ports. All the other combinations are okay. 

Thanks for reading and for any help! :)

---

