---
title: "t-mobile dash"
date: 2008-01-02
forum: North Carolina Team - US
---

### Post by Greymouser on 2008-01-02
I am very new to Ubuntu. I am using 7.10 on my Sony Viao VGA-FZ285U. I have a T-Mobile Dash (HTC S620) phone that I use to connect though my USB with Vista. Trying to get away from Windows and use Ubuntu. How do I connect my Dash phone to my computer using Ubuntu 7.10 through my USB. Thank you for time in this matter.

Very Respectfully,
Jackie

---

### Post by e30drift on 2008-01-30
me too!!  

I would really like to use it as a wireless modem when im on the road.
syncing would be sweet too.

---

### Post by Yggdrasil_ on 2008-05-14
Me too.
I have played with the verizon stuff and it has something to do with lsmod and then modprobing the usbserial with a proper code.
However since i dont think you have to do a chap authentication it might be somethign different.

---

### Post by jfrorie on 2008-05-15
> **Yggdrasil_ said:**
> Me too.
I have played with the verizon stuff and it has something to do with lsmod and then modprobing the usbserial with a proper code.
However since i dont think you have to do a chap authentication it might be something different.

IIRC, Most mobile phone should work off the USB serial driver. I think Gnome-PPP will drive it.  I used KPPP under gnome and it works fine with a razr.  You will need the authentication parameters (Username/password)  I have the Razr working fine.

See if this sheds some light...
[http://ubuntuforums.org/archive/index.php/t-556191.html](http://ubuntuforums.org/archive/index.php/t-556191.html)


As for sync, if you have mobile web access, funambol.com has a number of solutions that will work over the air if your phone supports SyncML.
Jim

---

### Post by Yggdrasil_ on 2008-05-15
Ok guys. Just to be clear on this, I think the idea setup would be not to use any form of "dialup" but use this as a network card. 
It took me a bit because I wasnt sure how the process worked under windows.
My suspicion was right that it does create a network card the somehow obtains an ip from the cell phone. I use a cooked rom (msg me if you need to know about this) and it has an app called internet sharing not sure if the tmobile rom has this but here is a link for that. Once you run and connect this software it start the virtual network card.
Good news and bad news.
Good news is I think its possible.
Bad news is if your like me and use the 5.99 tmobile internet plan the only way it works is to use a proxy on the app your using.
So i'm thinking of upgrading to the 20 dollar plan which i verified works perfectly.
Now something interesting.
There is this piece of software : WMWifiRouter 
It basicly turns the cell phone into some sort of ad hock wireless access point.
It isnt free but if it works its cool and that should solve most problems.
As for connecting over usb here is some output that I got out of my dmesg
 
OUtput:
[106200.854005] usb 2-1: USB disconnect, address 6
[174295.649118] usb 2-1: new full speed USB device using uhci_hcd and address 7
[174295.818191] usb 2-1: configuration #1 chosen from 1 choice
[174298.434704] usb 2-1: USB disconnect, address 7
[174301.771704] usb 2-1: new full speed USB device using uhci_hcd and address 8
[174301.940078] usb 2-1: configuration #1 chosen from 1 choice
[174442.195472] usb 2-1: USB disconnect, address 8
[174445.536506] usb 2-1: new full speed USB device using uhci_hcd and address 9
[174445.704572] usb 2-1: configuration #1 chosen from 1 choice
[174453.417550] usb 2-1: USB disconnect, address 9
[174456.758569] usb 2-1: new full speed USB device using uhci_hcd and address 10
[174456.927597] usb 2-1: configuration #1 chosen from 1 choice

thats the dmesg after plugging it in and out a few times
May 15 10:04:11 localhost kernel: [174596.646800] usb 2-1: USB disconnect, address 10
May 15 10:04:11 localhost NetworkManager: <debug info>^I[1210867451.234181] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_bb4_303_a8c40305_58f9_0103_6800_0050bf3f5173_if0'). 
May 15 10:04:11 localhost NetworkManager: <debug info>^I[1210867451.252883] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_bb4_303_a8c40305_58f9_0103_6800_0050bf3f5173_if1'). 
May 15 10:04:11 localhost NetworkManager: <debug info>^I[1210867451.274120] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_bb4_303_a8c40305_58f9_0103_6800_0050bf3f5173_usbraw'). 
May 15 10:04:11 localhost NetworkManager: <debug info>^I[1210867451.289466] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_bb4_303_a8c40305_58f9_0103_6800_0050bf3f5173'). 

thats var/log/syslog
lsusb
yggdrasil@ubuntu:~$ lsusb
Bus 002 Device 012: ID 0bb4:0303 High Tech Computer Corp. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
yggdrasil@ubuntu:~$ 


Good luck guys.
ps I think this will also work for most of the tmobile windows based phones.

---

### Post by jfrorie on 2008-05-15
> **Yggdrasil_ said:**
> Ok guys. Just to be clear on this, I think the idea setup would be not to use any form of "dialup" but use this as a network card. 



I'm not sure if Verizon is EVDO OR GSM, but from what I remember, the phone doesn't "dialup", it connects to a digital network using AT commands, emulating a modem.  PPP handles this, creates the necessary gateway connection and even handles the router exceptions so you can use multiple networks.

I think the solution that you are describing is identical, with the exception of the dialup latency.  PPP would be better for people that don't have unlimited plans and it doesn't require proxy configurations.

---

### Post by Yggdrasil_ on 2008-05-20
Dialup would be going to 56k (if that). Ill see if I get some time to dig into it a bit further.
The wireless software seems like the way to go.

---

### Post by jfrorie on 2008-05-20
> **Yggdrasil_ said:**
> Dialup would be going to 56k (if that). Ill see if I get some time to dig into it a bit further.
The wireless software seems like the way to go.

I clocked a Razr over KPP at about 500K peak.  It's quite usable for email and web access.  

Dialup in traditional "MODEM" sense doesn't apply.  Modems aren't used on digital networks as they modulate digital signals over analog lines.  The cell network is fully digital now. It's similar to an ISDN line, IIRC.  I think the nomenclature and commands are used for legacy reasons.

I think both methods use the same comm path, it's just a matter of the authentication and billing for the mobile provider.

Again, my experience is with EVDO. YMMV

---

