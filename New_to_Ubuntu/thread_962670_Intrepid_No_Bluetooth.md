---
title: "Intrepid No Bluetooth"
date: 2008-10-29
forum: New to Ubuntu
---

### Post by mevets on 2008-10-29
So bluetooth has never worked out of the box for me on any version of ubuntu. It has not been until now that I have the urge to get it working as I have a nokia n800 and it rocks to type out a text message and then send it.

I have a Gateway mx6931 which is supposed to have bluetooth but I dont know how to go about getting it to work. The bluetooth chip is a Gateway WidComm Bluetooth device.

Theres no mention of bluetooth on the specs page but theres a driver on the downloads page for xp.
[http://support.gateway.com/support/drivers/mydl.asp?tab=MY&os=Windows%20XP](http://support.gateway.com/support/drivers/mydl.asp?tab=MY&os=Windows%20XP)

Has anyone had luck fixing bluetooth using hardware like mine?

---

### Post by LowSky on 2008-10-30
please run this command from terminal
```
lspci
```

It will let us know what type of bluetooth controller you have exactly

---

### Post by isecore on 2008-10-30
I'm going to shamelessly plug [my own thread]("http://ubuntuforums.org/showthread.php?t=962254") where I also complain about bluetooth not working in Intrepid. Worked fine for me in Hardy, after upgrade no more bluetooth.

---

### Post by erlguta on 2008-10-31
I have the same problem.
I can't send files from my mobile to intrepid. In Hardy it worked perfectly.

---

