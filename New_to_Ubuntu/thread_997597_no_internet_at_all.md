---
title: "no internet at all"
date: 2008-11-30
forum: New to Ubuntu
---

### Post by ja660k on 2008-11-30
Just brought a new compaq laptop with vista(lame) and it doesnt come witha recovery disk it has a option to recover, however i put ubuntu on it and i dont have any connection at all

i tried to run 
```

sudo dhclient eth0

```
that didnt work, i tried iwconfig all it says is no wireless extensions

i dno what to do

---

### Post by jpoRS on 2008-11-30
does anything show up when you input 

```
iwlist scan
```

jim

---

### Post by ja660k on 2008-11-30
interface doesnt support scanning.

ut comes up with
hardware drivers.

the LAN and wireless lan are being controlled by ubuntu...

i have no idea where the drivers for it can be


i think i have a big problem it says that these drivers ubuntu doesnt have

---

### Post by ja660k on 2008-11-30
update and bump. i got it to work under wired connection and i installed ndiswrapper and the gui for it, as well as knetworkmanager..

i installed the driver like normal it says it works, but now knetworkmanager cannot find my wireless router..? and i know its there because i have another ubuntu box and it works just fine...

please help..?


when i run iwconfig... and iwlist scan i dont seem to have a wlan0;
i only have lo and eth0

how can i resolve this..?

---

### Post by sharks on 2008-11-30
try this:
sudo pppoeconf

---

### Post by ja660k on 2008-11-30
"sorry I scanned 1 interface, but the access concentrator of your provider did not respond, please check your network and model cables. Another reason for a sacn failure may be another running pppoe process which controls the modem"


in the terminsl it also says /usr/sbin/pppoeconf: 520: modconf: not found

---

