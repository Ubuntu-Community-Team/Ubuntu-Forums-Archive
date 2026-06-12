---
title: "Plus TV Analog usb stick!"
date: 2008-01-25
forum: Philippine Team
---

### Post by sawewe_08 on 2008-01-25
is there someone know how to install the driver of **plus tv analog usb stick **(kworld).?pls help..thank you in advance!

---

### Post by xeth_delta on 2008-01-25
You might want to know what exact hardware is inside the USB card. To that end, issue in a terminal a:
```
lsusb
```
It should be listed there. You can then search in the forum about how to configure it.

Hope this helped.

---

### Post by stanca on 2009-04-26
I've got working my webcam and the same usb kworld tv tuner with the same merged driver from here: [http://linuxtv.org/hg/~jfrancois/gspca/](http://linuxtv.org/hg/~jfrancois/gspca/) .
Just take the bz2 package from above,extract it and compile/install it,reboot and then just they really work.
The only problem who still persists is that you can't have both working in the same time,if you want to watch your tv channels you have to unplugg the webcam first.
It works very well with tvtime.:popcorn:

---

