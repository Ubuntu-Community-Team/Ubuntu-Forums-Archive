---
title: "help w/ connect my wlan0"
date: 2008-08-25
forum: New to Ubuntu
---

### Post by determinedblkman on 2008-08-25
ok i unpacked, compiled, and installed "ndiswrapper" (1st time after many tries installing anything),then loaded my driver(and it was verified) but now i dont know how to connect(configure) it

 i'm usind "absolute linux" (slackware) 
 ...help please  (damn man pages are too verbose!!!!)

---

### Post by darrelljon on 2008-08-27
Get to a terminal and type.
```
lshw -C network
```
Identify your interface. Then type the following commands.
```
sudo ifconfig <interface> down
sudo dhclient -r <interface>
sudo ifconfig <interface> up
sudo iwconfig <interface> essid "ESSID_IN_QUOTES"
sudo iwconfig <interface> mode Managed
sudo dhclient <interface>
```
On mine for example I type.
```
sudo ifconfig ath0 down
sudo dhclient -r ath0
sudo ifconfig ath0 up
sudo iwconfig ath0 essid "linksys"
sudo iwconfig ath0 mode Managed
sudo dhclient ath0
```
That should work on an unencrypted connection. On a WEP connection you need.
```
sudo ifconfig <interface> down
sudo dhclient -r <interface>
sudo ifconfig <interface> up
sudo iwconfig <interface> essid "ESSID_IN_QUOTES"
sudo iwconfig <interface> key HEX_KEY
sudo iwconfig <interface> mode Managed
sudo dhclient <interface>
```
[Taken from these instructions]("http://ubuntuforums.org/showthread.php?t=684495"). I'm assuming since these are kernel commands they will work on any distro. There are graphical ways too.

---

