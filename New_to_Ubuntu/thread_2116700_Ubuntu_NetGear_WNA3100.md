---
title: "Ubuntu NetGear WNA3100"
date: 2013-02-16
forum: New to Ubuntu
---

### Post by SPhoenix2148 on 2013-02-16
Hi!
I'm a complete newb to Ubuntu and Linux and I have a prob that I need help with.
I just installed Ubuntu today alongside Windows 7 and I've been trying to connect to my network, I've looked at multiple vids and none solved my problem so I'm turning to you guys. I have a Netgear WNA3100 WiFi adapter and I've seen there are some problems with it and that you have to install some drivers but since I am a BIG newb at Linux/Ubuntu I need all the help I can get. I need fixes that work without an internet connection or maybe stuff that I can download on Windows or whatever any help is good!
Sincerely SPhoenix

---

### Post by carl4926 on 2013-02-16
In a terminal do

```
lsusb -v
```

Post back here, just the Netgear info

---

### Post by SPhoenix2148 on 2013-02-16
I typed lsusb and this is what I got: Bus 006 Device 003: ID 0846: 9020 NetGear, Inc. WNA3100(v1) Wireless-N 300 [Broadcom BCM43231]
Hope that was what you where after

---

### Post by carl4926 on 2013-02-16
> **SPhoenix2148 said:**
> I typed lsusb and this is what I got: Bus 006 Device 003: ID 0846: 9020 NetGear, Inc. WNA3100(v1) Wireless-N 300 [Broadcom BCM43231]
Hope that was what you where after

Is that all the info for the netgear?

This is info we can use: Broadcom BCM43231
But I don't see it listed here: [http://wireless.kernel.org/en/users/Drivers/b43](http://wireless.kernel.org/en/users/Drivers/b43)
Which doesn't look promising.

Personally I wouldn't waste my time with a device that doesn't work Out of the Box.
Get something like: (Belkin F5D7050)

---

### Post by SPhoenix2148 on 2013-02-17
Looks like I have to buy a new wireless adapter. Is that Belkin adapter any good? I might be able to get one tomorrow (18/02) so I need to know.

---

### Post by carl4926 on 2013-02-17
> **SPhoenix2148 said:**
> Looks like I have to buy a new wireless adapter. Is that Belkin adapter any good? I might be able to get one tomorrow (18/02) so I need to know.

Yes
Works out of the box

---

