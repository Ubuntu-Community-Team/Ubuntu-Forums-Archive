---
title: "Only 1 of 3 USB ports is working with 12.04 &amp; old Presario"
date: 2012-10-14
forum: New to Ubuntu
---

### Post by Kmargo945 on 2012-10-14
Hello,

I Recently installed 12.04 on an old Presario F700 laptop that belonged to my daughter. It was running Windows before I did a clean install of Ubuntu 12.04. Only 1 of 3 USB ports is working. She doesn't remember if this was the case when she had it and I'm trying to figure out if it's a hardware issue or not.

 lsusb:

[COLOR=Red]Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 0461:4d4c Primax Electronics, Ltd[/COLOR]

I realize the last line shows the wireless adapter for the mouse, which is working. I don't know what the rest means. There is an 8gb flash drive in one of the other ports that isn't showing up, I think it should be on Bus 001.

Thanks for your time,
Raul 

[http://paste.ubuntu.com/1280219](http://paste.ubuntu.com/1280219)

---

### Post by NikTh on 2012-10-14
Can you post the results***** of ```
lsusb -t
```

*****put the results between the brackets [noparse]```
Here
```[/noparse]

Thanks

---

### Post by squakie on 2012-10-14
Try moving the wireless mouse receiver to each of the "not working" USB ports and see what that does.  If no change, then obviously there is a problem to dig into more, as per NikTh.

---

### Post by Kmargo945 on 2012-10-15
> **squakie said:**
> Try moving the wireless mouse receiver to each of the "not working" USB ports and see what that does.  If no change, then obviously there is a problem to dig into more, as per NikTh.

Did that. It didn't work. Also plugged in the flash drive to the working port and it lit up right away.

lsusb -t:

```
/:  Bus 02.Port 1: Dev 1, Class=root_hub, Driver=ohci_hcd/8p, 12M
    |__ Port 1: Dev 2, If 0, Class=HID, Driver=usbhid, 1.5M
/:  Bus 01.Port 1: Dev 1, Class=root_hub, Driver=ehci_hcd/8p, 480M
```

Thanks for the quick responses.

---

### Post by NikTh on 2012-10-15
> **Kmargo945 said:**
> 
```
/:  Bus 02.Port 1: Dev 1, Class=root_hub,** Driver=ohci_hcd**/8p, 12M
    |__ Port 1: Dev 2, If 0, Class=HID, Driver=usbhid, 1.5M
```
> **Kmargo945 said:**
> [COLOR=Red]
[/COLOR]```
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation **1.1 root hub**
```[COLOR=Red]
[/COLOR][IMG]http://paste.ubuntu.com/1280219/[/IMG]

Tell her that this port is a deprecated old usb 1.1 port and probably is not supporting Usb 2.0 flash - sticks.. All sticks these days are from usb 2.0 interface and up. 

[http://en.wikipedia.org/wiki/OHCI#Open_Host_Controller_Interface_2](http://en.wikipedia.org/wiki/OHCI#Open_Host_Controller_Interface_2),

If I am wrong , hopefully someone will correct me :)

---

### Post by newb85 on 2012-10-15
Removed!

---

### Post by audiomick on 2012-10-15
> **NikTh said:**
> Tell her that this port is a deprecated old usb 1.1 port and probably is not supporting Usb 2.0 flash - sticks.. All sticks these days are from usb 2.0 interface and up. 

[http://en.wikipedia.org/wiki/OHCI#Open_Host_Controller_Interface_2](http://en.wikipedia.org/wiki/OHCI#Open_Host_Controller_Interface_2),

If I am wrong , hopefully someone will correct me :)

I had that with my scanner. It only works on one port on my desktop. Have you got some old USB thing, maybe an older mouse or something, that you can use to cross check that theory?

---

### Post by Kmargo945 on 2012-10-15
> **NikTh said:**
> Tell her that this port is a deprecated old usb 1.1 port and probably is not supporting Usb 2.0 flash - sticks.. All sticks these days are from usb 2.0 interface and up. 
If I am wrong , hopefully someone will correct me :)

Had to look up deprecated.

I'm not sure if my 8gb flash drive (PNY) is 1.0 or 2.0 but it lights up as soon as I plug it into the only working port.

Let me see if I understand whats going on,

I have 1 usb 1.1 hub with two ports, one works, one doesn't. I'm guessing the 2 ports on the left side of the computer are off the same hub and are 1.1.

I have 1 usb 2.0 hub with one port which doesn't work on the right side.

Since one of the 1.1 ports works I'm guessing that's a hardware issue.

What  about the 2.0 port? Since it shows up on both lsusb and lsusb -t, I'm  guessing it's being recognized but nothing connected to it works.  So...hardware problem?

Thanks for the help,
Raul

---

### Post by audiomick on 2012-10-15
Well, that is possible, I suppose. I think it is more likely that the only port that is working is associated with the USB 2.0 hub, and the ones that aren't are associated with the 1.1 hub.

---

### Post by NikTh on 2012-10-16
> **Kmargo945 said:**
> Had to look up deprecated.
Let me see if I understand whats going on,

I have 1 usb 1.1 hub with two ports, one works, one doesn't. I'm guessing the 2 ports on the left side of the computer are off the same hub and are 1.1.

I have 1 usb 2.0 hub with one port which doesn't work on the right side.

Since one of the 1.1 ports works I'm guessing that's a hardware issue.

What  about the 2.0 port? Since it shows up on both lsusb and lsusb -t, I'm  guessing it's being recognized but nothing connected to it works.  So...hardware problem?


No, what I said is that you have 1 usb 1.1 hub with two ports (no matter if one is the left and one in the right of Laptop) which none of them working.

You have 1 usb 2.0 hub with one port and its working. 

If I am right , then a Usb 1.1 interface stick (or keyboard or mouse or something else , but must support 1.1 usb interface) will work in the 2 ports. If you manage to find something .. (difficult in our days) test it.

Interesting info we can collect from dmesg. 

Do this. 

Plug in your Usb 8GB (of course in one of the non working ports) and then open a terminal and give this command
```
dmesg | tail -n 25
```post the results back here.

Thanks

---

### Post by Kmargo945 on 2012-10-16
> **NikTh said:**
> No, what I said is that you have 1 usb 1.1 hub  with two ports (no matter if one is the left and one in the right of  Laptop) which none of them working.

You have 1 usb 2.0 hub with one port and its working. 

Okay, my mistake. In order to understand what it is that I'm supposed to  have I looked around the web and found one site listing the usb specs as all three being 2.0. Based on the replacement part specs from  HP, the one on the right (not integrated and not working) is a 2.0 so  I'm guessing they are all *supposed to be *2.0. I have no idea if any of this helps.

I thought I had an old mouse somewhere, but I can't find it.

Here's dmesg | tail -n 25

```
[   21.216387] type=1400 audit(1350397039.611:15):  apparmor="STATUS" operation="profile_load"  name="/usr/lib/telepathy/mission-control-5" pid=1003  comm="apparmor_parser"
[   21.217107] type=1400 audit(1350397039.611:16): apparmor="STATUS"  operation="profile_load" name="/usr/lib/telepathy/telepathy-*" pid=1003  comm="apparmor_parser"
[   21.373768] type=1400 audit(1350397039.767:17): apparmor="STATUS"  operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=1004  comm="apparmor_parser"
[   21.374470] type=1400 audit(1350397039.767:18): apparmor="STATUS"  operation="profile_load" name="/usr/sbin/cupsd" pid=1004  comm="apparmor_parser"
[   21.404108] ppdev: user-space parallel port driver
[   21.510574] type=1400 audit(1350397039.903:19): apparmor="STATUS"  operation="profile_load" name="/usr/sbin/mysqld-digikam" pid=1009  comm="apparmor_parser"
[   21.510921] type=1400 audit(1350397039.903:20): apparmor="STATUS"  operation="profile_load"  name="/usr/sbin/mysqld-digikam///usr/sbin/mysqld" pid=1009  comm="apparmor_parser"
[   21.892310] Bluetooth: Core ver 2.16
[   21.892350] NET: Registered protocol family 31
[   21.892353] Bluetooth: HCI device and connection manager initialized
[   21.892358] Bluetooth: HCI socket layer initialized
[   21.892361] Bluetooth: L2CAP socket layer initialized
[   21.892370] Bluetooth: SCO socket layer initialized
[   21.921417] Bluetooth: RFCOMM TTY layer initialized
[   21.921426] Bluetooth: RFCOMM socket layer initialized
[   21.921429] Bluetooth: RFCOMM ver 1.11
[   21.950163] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   21.950168] Bluetooth: BNEP filters: protocol multicast
[   24.329773] forcedeth 0000:00:14.0: eth0: no link during initialization
[   24.337134] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   24.340467] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   30.161691] init: anacron main process (1115) killed by TERM signal
[   34.093585] init: plymouth-stop pre-start process (1405) terminated with status 1
[  104.320061] eth2: no IPv6 routers present
[  107.932046] CE: hpet increased min_delta_ns to 11520 nsec
```

Thanks

---

### Post by NikTh on 2012-10-16
I cannot see anything. If you connected a usb-stick its like not connected (never). 

Can you try with the newest Ubuntu kernel 3.5 ? (Ubuntu 12.10). Is not necessary to install something.

Download the .iso image and burn it to a CD-or-Usb and boot from there and do the same thing. 
Connect a Usb-stick and then open a terminal and give the result 
```
dmesg | tail -n 25
```

You can find the latest .iso here: [http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

Besides what you've found in Web , the Linux kernel recognized 2 Usb hubs. One with usb1.1 interface and 1 with usb2.0 interface. That the  hub with usb1.0 interface has 2 ports is only my guess. 

Thanks

---

### Post by Kmargo945 on 2012-10-17
Here's dmesg | tail -n 25 with the new kernel, three flash drives plugged in, booted off usb.

```
ubuntu@ubuntu:~$ dmesg | tail -n 25
[ 2256.284082] hub 1-0:1.0: >connect-debounce failed, port 2 disabled
[ 2258.204066] hub 1-0:1.0: >connect-debounce failed, port 2 disabled
[ 2260.128063] hub 1-0:1.0: >connect-debounce failed, port 2 disabled
[ 2262.048097] hub 1-0:1.0: >connect-debounce failed, port 2 disabled
[ 2263.968086] hub 1-0:1.0: >connect-debounce failed, port 2 disabled
[ 2265.892081] hub 1-0:1.0: >connect-debounce failed, port 2 disabled
[ 2267.812068] hub 1-0:1.0: >connect-debounce failed, port 2 disabled
[ 2269.736071] hub 1-0:1.0: >connect-debounce failed, port 2 disabled
[ 2271.656069] hub 1-0:1.0: >connect-debounce failed, port 2 disabled
[ 2273.580079] hub 1-0:1.0: >connect-debounce failed, port 2 disabled
[ 2275.500072] hub 1-0:1.0: >connect-debounce failed, port 2 disabled
[ 2277.420070] hub 1-0:1.0: >connect-debounce failed, port 2 disabled
[ 2279.344071] hub 1-0:1.0: >connect-debounce failed, port 2 disabled
[ 2281.264079] hub 1-0:1.0: >connect-debounce failed, port 2 disabled
[ 2283.188082] hub 1-0:1.0: >connect-debounce failed, port 2 disabled
[ 2285.108067] hub 1-0:1.0: >connect-debounce failed, port 2 disabled
[ 2287.028089] hub 1-0:1.0: >connect-debounce failed, port 2 disabled
[ 2288.952094] hub 1-0:1.0: >connect-debounce failed, port 2 disabled
[ 2290.872081] hub 1-0:1.0: >connect-debounce failed, port 2 disabled
[ 2292.796070] hub 1-0:1.0: >connect-debounce failed, port 2 disabled
[ 2294.716065] hub 1-0:1.0: >connect-debounce failed, port 2 disabled
[ 2296.640073] hub 1-0:1.0: >connect-debounce failed, port 2 disabled
[ 2298.560078] hub 1-0:1.0: >connect-debounce failed, port 2 disabled
[ 2300.480104] hub 1-0:1.0: >connect-debounce failed, port 2 disabled
[ 2302.404101] hub 1-0:1.0: >connect-debounce failed, port 2 disabled
```

---

### Post by Kmargo945 on 2012-10-26
According to this thread:

[https://bbs.archlinux.org/viewtopic.php?id=111464](https://bbs.archlinux.org/viewtopic.php?id=111464)

It looks like a hardware issue. Thanks everyone for the help.

Raul

---

