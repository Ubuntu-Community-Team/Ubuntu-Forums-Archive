---
title: "USB mouse doesn't work with my own build of Ubuntu"
date: 2016-05-22
forum: New to Ubuntu
---

### Post by Sam_Rosewood on 2016-05-22
Hello!
I made my own build of Ubuntu 16.04 x64 using this manual ([https://help.ubuntu.com/community/LiveCDCustomization](https://help.ubuntu.com/community/LiveCDCustomization)).
Almost everything is alright, but I found that USB mouse doesn't work with the build. There is no cursor and reaction to clicking (neither in install wizard nor in LiveCD mode), but the mouse lights and indicates its moving. PS/2 mouse and keyboard work with the build normally.
Both mice (USB and PS/2) work normally with the official image of Ubuntu 16.04 x64.
How can I make a build with saving ability to use USB mouse, like in the official image? This bug really upsets me.

---

### Post by mastablasta on 2016-05-23
is the mouse recognised among listed USB devices?

```
lsusb
```


Are the USB drivers loaded on boot?

---

### Post by Sam_Rosewood on 2016-05-23
I loaded from two flash drives: my build and official image.
Here is the log, it's same in both cases.

ubuntu@ubuntu:~$ lsusb
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 058f:6387 Alcor Micro Corp. Flash Drive
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 002: ID 09da:000a A4Tech co., Ltd. Optical Mouse Opto 510D / 0P-620D
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 04f3:0103 Elan Microelectronics Corp. ActiveJet K-2024 Multimedia Keyboard
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Both systems see USB mouse, but it doesn't work with my build. Though it lights when I move it, but there is no cursor and reaction.
P.S. By the way, when I made screenshots of logs, I saw that my build doesn't reproduce the sound of taking as it should, like in official image. So here is another problem with sound.

---

