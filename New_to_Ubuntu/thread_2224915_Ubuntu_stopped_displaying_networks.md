---
title: "Ubuntu stopped displaying networks"
date: 2014-05-18
forum: New to Ubuntu
---

### Post by chris221 on 2014-05-18
So, my linksys wusb100 adapter has even doing fine for the past couple weeks that I've had Ubuntu, but all the sudden I get on my computer today and it tells me it's disconnected, so I go to the network manager and it isn't showing any available networks, anyone know how to fix this?

---

### Post by grahammechanical on 2014-05-19
If Network Manager is not showing any networks or wireless access points then it could mean that the WiFi adapter is disabled or even switched off. Is Ubuntu the only operating system on this machine. I have heard that if networking/WiFi is switched off in Windows then it remains switched off in Ubuntu. Make sure that networking and Wi-Fi are enabled. There are some commands we can run.

```
rfkill unblock wifi
```

```
sudo ifconfig wlan0 down
```
followed by 
```
sudo ifconfig wlan0 up
```

This command will give you a clue as to the problem.

```
rfkill list
```

This is what you should see.

> 0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no




Blocked in software can mean that WiFi is not enabled or there is not a driver for the wireless adapter. Blocked in hardware can mean that the wireless adapter is switch off by some kind of hardware (physical) switch mechanism.

Regards.

---

### Post by chris221 on 2014-05-21
So those commands gave me an error and I didn't get expected out put, I am solely running Ubuntu also. I think the problem may be my adapter because I plugged it into my other comp and it came out as an unknown device when it usually works on that computer, also when I run lsusb I get no line showing that it's detected, so is it possibly disabled or something? Thanks for the reply

---

### Post by squakie on 2014-05-21
If it's not showing in lsusb, it may well be a bad adapter.  As far as I know, lsusb shows any usb hardware it can identify, no matter if there's a driver, etc..  It should be showing any usb hardware.  Is it possible there's some sort of physical on/off switch on the device itself?

---

### Post by chris221 on 2014-05-21
Well it's showing up on my windows computer as an "Unknown Device" and the light comes on on the adapter but my computer must not be detecting it

---

### Post by squakie on 2014-05-21
Did it work before in the same Windows installation?  No driver was removed, etc.?  Different usb ports and still the same problem?  If so, you may be having a hardware problem.

I don't normally comment on devices to try, but if you need to try a new device I would try the Tenda USB W322U.  I have used several of those (less than $15 when I've bought them) from Micro Center.

---

