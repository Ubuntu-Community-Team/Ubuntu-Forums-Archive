---
title: "Web Cam on Netbook Won't Work"
date: 2012-06-07
forum: New to Ubuntu
---

### Post by n00bi on 2012-06-07
Hi All

After my latest encounter with installing the keyboard, now that everything works fine, I have a new challenge.

1- The Acer 250D built in webcam won't get recognized
2- When i close the lid down, the screen turns off and flickers if i press a button or move the mouse!

I would appreciate any expert help on any of the above.

Thanks

---

### Post by papibe on 2012-06-07
Hi n00bi.

Have you tried the the 'LD_PRELOAD' trick?

For example, to launch skype:
```
LD_PRELOAD=/usr/lib/i386-linux-gnu/libv4l/v4l1compat.so  /usr/bin/skype
```

If that doesn't work, could you post the result of this command:
```
lsusb
```
Regards

---

### Post by n00bi on 2012-06-07
[FONT=monospace]mem0r1es@mem0r1es-Aspire-one:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 0d8c:0105 C-Media Electronics, Inc. CM108 Audio Controller
Bus 003 Device 002: ID 04f3:0103 Elan Microelectronics Corp. 
Bus 003 Device 003: ID 0461:4d17 Primax Electronics, Ltd Optical Mouse
Bus 005 Device 002: ID 0a5c:2101 Broadcom Corp. Bluetooth Controller

[/FONT]

---

