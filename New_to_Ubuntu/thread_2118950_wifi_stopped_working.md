---
title: "wifi stopped working"
date: 2013-02-22
forum: New to Ubuntu
---

### Post by Brutus Blutoski on 2013-02-22
installed Ubuntu 12.10 and everything was working fine.....then the wifi stopped working but everything else seems to be fine, just can't connect to the internet......the upper right hand indicator in Ubuntu shows no wifi signal at all.....the message I am getting during start up is the wifi is disconnected and that I am off-line.........the wifi indicator light is red and does not change to blue......the message in the wifi control panel is wifi is un-managed........
 
I know it's possible that the wifi card could have failed for some reason but I don't know how to check to see if it's ok or not......went to a computer store and they wanted $35 to check it to see if it's ok - told them to stuff it - I can buy a new card for less than that.......
 
before buying a new card and relacing the one that came with the puter I was wondering if anyone may have an idea as to why the wifi is not working and went out while I was on-line........
 
Don't know if this helps......Hewlett Packard Pavilion g6.....the only operating system I am running is Ubuntu 12.10......
 
just want to get my wifi back up and running........

---

### Post by DuckHook on 2013-02-23
We need much more info about your system. Otherwise, stumbling around in the dark. Please open a terminal using <Ctrl>+<Alt>+<t> and do:
```
sudo lshw -C network
``````
sudo lspci -vk | grep -iA13 net
``````
ifconfig
``````
iwconfig
``````
cat /etc/modules
``````
grep blacklist /etc/modprobe.d/blacklist.conf
```The output will be considerable, so for easier reading, highlight each set of outputs and wrap it in a "code" box just like I have by using the hash (#) character at the top of the posting box. Please give each output its own hash tags.

Also, did this happen after an update? Did you install any new software prior to problem? Need all details you can remember or think relevant.

---

