---
title: "Bluetooth receiver not coming up automatically"
date: 2011-09-13
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Yfrwlf on 2011-09-13
[COLOR="Red"]Problem 1[/COLOR]: The bluetooth settings Gnome window should be able to turn on / bring up bluetooth devices, and it's not able to bring up mine until I do the following using hciconfig.

[COLOR="Red"]Problem 2[/COLOR]: The bluetooth settings Gnome window should be responsive to clicking the bluetooth on/off button, but it only reports the change after closing and re-opening the window.


Starting a new thread as this specific issue seems to be different from other bluetooth issues currently going on.  When I plug in my bluetooth receiver, it makes the bluetooth icon appear.  But in bluetooth settings, it shows bluetooth as being OFF.  The problem is, I can't turn it on by clicking on it.  The settings window also doesn't show any paired devices.  The only way I've found to turn it on is by using hciconfig.

```
$ hciconfig
hci0:	Type: BR/EDR  Bus: USB
	BD Address: 00:00:00:00:00:00  ACL MTU: 0:0  SCO MTU: 0:0
	DOWN 
	RX bytes:0 acl:0 sco:0 events:0 errors:0
	TX bytes:0 acl:0 sco:0 commands:0 errors:0
```

Notice that "BD Address" and all info is blank.

```
$ hciconfig hci0 up
$ hciconfig
hci0:	Type: BR/EDR  Bus: USB
	BD Address: 00:1F:81:00:08:30  ACL MTU: 1021:4  SCO MTU: 180:1
	UP RUNNING PSCAN 
	RX bytes:1014 acl:0 sco:0 events:28 errors:0
	TX bytes:622 acl:0 sco:0 commands:27 errors:0
```

Then everything works fine.  Back in bluetooth settings, it showed it as being turned on.  I can then turn it off, and back on again using the bluetooth settings window (however, I have to close and then re-open the window as the change doesn't show up in the window (problem #2)).  When I turn it off in the settings window, hciconfig shows it as down again, but it has a "BD Address", and other status information for it.

So, when connecting the receiver, it's not turning on bluetooth, and that is how it should be AFAIK.  However, hciconfig is able to bring it up even though it's somehow not "fully registered" (?) yet, but the bluetooth settings window is not able to bring it up until hciconfig brings it up.  What is the difference between what the gnome bluetooth settings window is doing and what hciconfig is doing?  Is the hardware address for the device blank at first because that isn't reported until a device is powered on for the first time?

```
$ lsusb
Bus 005 Device 003: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
```

Anyone else having this problem in 11.10?

Thanks! ^^

---

### Post by CaptainMark on 2011-09-14
bluetooth seems a complete mess lately, seems its just an after thought, the option to change your device name has been completely removed and i havent been able to send or recieve any files since upgrading to 11.10

---

### Post by Yfrwlf on 2011-09-14
> **CaptainMark said:**
> bluetooth seems a complete mess lately, seems its just an after thought, the option to change your device name has been completely removed and i havent been able to send or recieve any files since upgrading to 11.10

I was able to send files to my phone, so maybe it's a driver issue with your bluetooth device, where it can see the device and you can pair and such, but the driver isn't good enough to do file transmission?  Just a guess, no clue. :confused:

I take that back, for me when I did "browse files on device", it locked up my whole computer.  Yay for the Linux kernel ONLY having good quality drivers theory (trying to justify having a constantly breaking driver ABI which is a bunch of BS)!  lol

However, when I did "send files to device", that worked.  On my phone it showed an incoming file and asked me where to save it, and even opened it after it was done transferring.  I have a N900.

---

### Post by CaptainMark on 2011-09-14
my bluetooth works flawlessly in natty, what a pain, i believe its the gnome3 bluetooth configuration thats at fault but to be honest this subject is far from my area so i could be talking rubbish

---

