---
title: "webcam"
date: 2021-07-18
forum: New to Ubuntu
---

### Post by amirabbasjadidi on 2021-07-18
Hello
I have an old webcam from the genius brand, but I did not find a driver for everything I searched on the internet.
Of course, I used lsusb and it gave the following answer
[COLOR=#000000][FONT=&amp]Bus 001 Device 004: ID 1a40:0101 Terminus Technology Inc. Hub[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]Bus 004 Device 002: ID 1c4f:0026 SiGma Micro Keyboard[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]Bus 003 Device 002: ID 18f8:0f99 [Maxxter] Optical gaming mouse[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]Bus 002 Device 002: ID 0c45:6005 Microdia Sweex Mini Webcam[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
[/FONT][/COLOR]Webcam is visible but it does not work in cheese, please help, thank you

---

### Post by ActionParsnip on 2021-07-21
If you boot the system without the webcam installed then log in. Let the system settle then plug in webcam. Press CTRL + ALT + T and run:
```

dmesg | tail ; lsb_release -a; uname -a

```
What is the output please?

---

### Post by ActionParsnip on 2021-07-21
Seems to need the sonixb kernel module

---

