---
title: "[eeebuntu] freshly installed, no internet"
date: 2013-05-11
forum: New to Ubuntu
---

### Post by Kalaskow on 2013-05-11
I've just installed EEEBuntu(also know as Aurora OS) onto my new Asus Netbook(R052CE / eeePc 1025ce). Now i want it to have internet to update its drivers. But it looks like there is no drivers for it installed, as I can neither use Lan or WLan. Also when i attach my USB-Stick to the device it doesn't look like its recongizing it.

So my Problem is. I have drivers missing, and i dont know which and how to get them on the device.

---

### Post by Hekabe on 2013-05-11
Can you see wireless networks? Use ```
sudo iwlist scan
``` in terminal and post the output.
As for the USB drive, connect it, then type "dmesg tail" in terminal, and post all lines beginning with [sdb], at least near the bottom.

---

