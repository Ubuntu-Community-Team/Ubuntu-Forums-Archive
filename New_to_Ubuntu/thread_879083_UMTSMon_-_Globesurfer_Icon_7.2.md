---
title: "UMTSMon - Globesurfer Icon 7.2"
date: 2008-08-03
forum: New to Ubuntu
---

### Post by Indizann on 2008-08-03
I'm quite new to Linux/Ubuntu and i'm trying to get my Globesurfer Icon 7.2 usb modem to work with my laptop with Ubuntu 8.04

I managed to compile Umtsmon, which detects the modem and even the network, but when trying to connect i keep receiving the same error: 

Using interface ppp0
Connect: ppp0 <--> /dev/ttyUSB0
LCP: timeout sending Config-Requests
Connection terminated.
Modem hangup

The stick is from Belgian mobile phone operator Mobistar, with apn iew.be

---

### Post by Indizann on 2008-08-04
anyone :(

---

### Post by c2olen on 2008-08-04
I've got this running, but i dont use UMTSmon to start the dialup. It give's me the same results you just posted.
Instead I use a ppp dialscript which you can start using Gnome-PPP.

You can also set up some udev rules to automatically initiate a dial in when you insert the UMTS device (either USB stick or Express Card).

I'll post my dial in scripts in a separate post. I am on another computer now, and do not like to retype it all.

---

### Post by c2olen on 2008-08-04
> **c2olen said:**
> 
I'll post my dial in scripts in a separate post. I am on another computer now, and do not like to retype it all.


Here they are.
```

c2olen@okinawa:~$ cat /etc/ppp/peers/ppp0
/dev/ttyUSB0
#/dev/rfcomm0
connect "/usr/sbin/chat -v -f /etc/chatscripts/ppp0"
novj
usepeerdns
crtscts
defaultroute
debug
nodeflate
noccp
noipdefault
noaccomp
115200
user "<your-provider-goes-here>"
persist

```

and the chatscript

```

c2olen@okinawa:~$ cat /etc/chatscripts/ppp0
ABORT 'BUSY' 
ABORT 'NO CARRIER' 
ABORT 'ERROR' 
'' AT 
OK AT+CGATT=1 
OK AT+CGDCONT=1,"IP","internet" 
OK      ATDT*99***1#c

```

You might need to change some settings to fit your provider, but it should get you on your way.

I've made this udev-rule to automatically start and stop PON on device connection and removal.
You will probably need to change your vendor specific ID's to match your device.

```

c2olen@okinawa:~$ cat /etc/udev/rules.d/50-globesurfer-icon.rules 
BUS=="usb", SYSFS{idProduct}=="1000", SYSFS{idVendor}=="05c6", RUN+="/usr/bin/icon_switch"
BUS=="usb", SYSFS{idProduct}=="6701", SYSFS{idVendor}=="0af0", RUN+="/sbin/modprobe usbserial vendor=0x0af0 product=0x6701"
KERNEL=="ttyUSB?", ACTION=="add", RUN+="/usr/bin/sudo -u c2olen /usr/bin/pon", SYMLINK+="modem"
KERNEL=="ttyUSB?", ACTION=="remove", RUN+="/usr/bin/sudo /usr/bin/poff -a"

```

---

