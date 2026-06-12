---
title: "Keyboard Compatibility"
date: 2014-06-12
forum: New to Ubuntu
---

### Post by dee7 on 2014-06-12
Keyboard wired usb Lenovo model SK-8825 (L) azerty (French) 'Restaurer l'état du verrouillage au démarrage' does not work . Bug or compatibility ? I assume the latter . Not a big problem but annoying as I fail to notice on login that the keyboard lock isn't on

---

### Post by sandyd on 2014-06-12
Hi, can you post the output of
```

lsusb
```
while the keyboard is plugged in?

Thanks!

---

### Post by dee7 on 2014-06-12
Yes done here it is:
```
Bus 001 Device 004: ID 06bc:0051 Oki Data Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 413c:3016 Dell Computer Corp. Optical 5-Button Wheel Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 04b3:3025 IBM Corp. NetVista Full Width Keyboard
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

---

### Post by dee7 on 2014-06-13
Got this info from wiki and it worked . Number lock can be run by changing configuration of **LightDM** display manager. Edit **/usr/share/lightdm/lightdm.conf.d/50-unity-greeter.conf** file and add the following line at the end: greeter-setup-script=/usr/bin/numlockx on  Obviously not a compatibilty problem

---

