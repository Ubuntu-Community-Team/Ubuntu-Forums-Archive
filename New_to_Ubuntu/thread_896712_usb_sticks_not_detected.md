---
title: "usb sticks not detected"
date: 2008-08-21
forum: New to Ubuntu
---

### Post by Malcoha on 2008-08-21
Hello everybody,

Under my brand new Hardi, my usb keys and external hard disk are not recognized at all. Nothing under lsusb, nothing happens with dbus-monitor--system when plugging/unplugging. BUT, my usb mouse works fine and is recognized with lsusb along with my webcam. The usb ports and the sticks are both OK since they work fine under Winxp on the same machine (dual boot).

Any idea for a poor newbie?

Thanks

---

### Post by gjoellee on 2008-08-21
there ma be a problem with the HAL detection, you should report this to launchpad.net and also this may be fixed in Intrepid or Linux Mint

---

### Post by philinux on 2008-08-21
> **Malcoha said:**
> Hello everybody,

Under my brand new Hardi, my usb keys and external hard disk are not recognized at all. Nothing under lsusb, nothing happens with dbus-monitor--system when plugging/unplugging. BUT, my usb mouse works fine and is recognized with lsusb along with my webcam. The usb ports and the sticks are both OK since they work fine under Winxp on the same machine (dual boot).

Any idea for a poor newbie?

Thanks


What are your system specs?

Plug in a stick then post the output of

```
dmesg | tail -30
```

Copy and paste the above code.

---

### Post by Energy Jobs on 2008-09-03
I never faced this problem.
but it is easy to detect.
1. Restart your system.
2. Install USB Driver (if not compatible)
3. Use the USB

Regards

---

### Post by Lorin Ricker on 2008-09-03
See also this thread on a similar problem & behavior:

  [http://ubuntuforums.org/showthread.php?t=908942](http://ubuntuforums.org/showthread.php?t=908942)

Let's compare notes and replies to these two threads...

---

