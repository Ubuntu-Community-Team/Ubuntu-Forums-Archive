---
title: "newb/wire wireless help/hardy"
date: 2008-07-30
forum: New to Ubuntu
---

### Post by azlinuxnb on 2008-07-30
newb needs help with connection trouble on hardy.  was messing around with network manager to get my wireless to connect automatically and now I can't connect at all wired or wireless.  tried to reinstall NM then installed kwifi removed both NM and kwifi.  can i go back to a previous configuration like on window or reinstall NM from the live cd without losing any data.  Any help would be appreciated.

---

### Post by darrelljon on 2008-08-27
I have lots of trouble with graphical network managers. Whenever I tried to set KNetworkManager to connect automatically, it refused to connect to wired or wireless network interface. I plan to work this out eventually. In the meantime try terminal commands.

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

