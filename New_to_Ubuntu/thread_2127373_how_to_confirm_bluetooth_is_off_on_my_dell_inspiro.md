---
title: "how to confirm bluetooth is off on my dell inspiron n5010"
date: 2013-03-19
forum: New to Ubuntu
---

### Post by cutSn8 on 2013-03-19
Hi I have ubuntu 12.04.2 amd64 installed on a dell inspiron n5010 and want to know how to confirm the bluetooth is turned off.  
I've noticed there's a bluetooth icon in the dash, but I don't really want to click on this in case it turns the bluetooth on and I can't work out how to turn it off.
When I had windows installed the computer would connect with any bluetooth devices in range (including e.g. mobile phones of passers by) if I left bluetooth on!
Thanks

---

### Post by DuckHook on 2013-03-20
```
rfkill list all
```

For your peace of mind, Bluetooth may not give you the same problem in Ubuntu. As far as I know, in Ubuntu, you must take active measures to pair before Bluetooth will connect to other devices. However, you are absolutely correct in your instinct to disable all services/exposures that you don't use. The best way to do this is to turn Bluetooth off in the BIOS.

---

### Post by coldraven on 2013-03-20
In 12.10 the Blue tooth icon will be the same colour as the wifi, battery, speaker and clock icons if it is ON.
When OFF it is more grey.
I just click the icon to do that!

---

