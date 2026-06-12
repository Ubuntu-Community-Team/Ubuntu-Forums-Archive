---
title: "Error after update 3.522387 mtd device"
date: 2022-07-23
forum: New to Ubuntu
---

### Post by billy3xs on 2022-07-23
After installing Ubuntu I updated and got this error [  3.522387] mtd device must be supplied (device name is empty)
[ubuntu] is in Boot Option #1

What do I do?
thanks

---

### Post by Dennis N on 2022-07-23
If your system boots up normally after the message appears, there's nothing to worry about. Just ignore it. It's because you probably don't have any mtd device on your system. Here is an article (from 10 years ago) that explains what such a device is. 

[https://www.opensourceforu.com/2012/01/working-with-mtd-devices/](https://www.opensourceforu.com/2012/01/working-with-mtd-devices/)

Messages in journal. The 2nd one appears briefly during startup before reaching login screen. The others do not.
```
Jul 23 06:22:48 Sydney-vm systemd[1]: Starting Load Kernel Module mtdpstore...
Jul 23 06:22:48 Sydney-vm kernel: mtd device must be supplied (device name is empty)
Jul 23 06:22:48 Sydney-vm systemd[1]: modprobe@mtdpstore.service: Deactivated successfully.
Jul 23 06:22:48 Sydney-vm systemd[1]: Finished Load Kernel Module mtdpstore.

```

---

### Post by billy3xs on 2022-07-23
Thanks, but the program hangs there and blinks.
Oh, the message disappeared, and a dash is blinking. Maybe it's processing.

---

### Post by Dennis N on 2022-07-23
There is a bug report here, with lots of comments to see:
[https://bugs.launchpad.net/ubuntu/+source/systemd/+bug/1981622](https://bugs.launchpad.net/ubuntu/+source/systemd/+bug/1981622)

It will probably get fixed sooner or later, but an option for a new installation that's badly affected (does not boot at all, or has an unwanted delay)  would be to install Ubuntu 20.04 LTS which doesn't have this problem. Its supported until 2025.

---

### Post by Impavidus on 2022-07-23
If it hangs, I suppose it's unrelated to that mtd message. That number (3.522387) is a timestamp. The message was generated about 3.5 seconds after starting the boot process.

FYI, that mtd message appears on my 22.04 system too – usually even twice. My timestamp is a bit higher. I suppose my computer is older/slower.

---

### Post by billy3xs on 2022-07-24
Ok I installed 20.04 and it still went to that problem.
However I went back into the BIOS and [ubuntu] was #1. I changed the order to something else and it works now!
When it booted there was that menu as if I had a dual boot set up, like before.

---

