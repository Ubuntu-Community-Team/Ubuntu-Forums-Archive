---
title: "Duplicated Serial Devices"
date: 2014-06-12
forum: New to Ubuntu
---

### Post by tjudsonesch on 2014-06-12
I'm brand new to ubuntu, and having issues trying to connect an external device via usb.  Basically every time I try to reconnect the device it creates a duplicate with the same name. 
For example, I run ```
dmesg | grep tty
```

and I get
> [    0.324549] console [tty0] enabled
[  107.427130] cdc_acm 2-1:1.0: ttyACM0: USB ACM device
[  330.361424] cdc_acm 2-1:1.0: ttyACM0: USB ACM device
[ 1386.437487] cdc_acm 2-1:1.0: ttyACM0: USB ACM device
[ 1477.059065] cdc_acm 2-1:1.0: ttyACM0: USB ACM device
[ 2816.623034] cdc_acm 2-1:1.0: ttyACM0: USB ACM device
[ 2870.348488] cdc_acm 2-1:1.0: ttyACM0: USB ACM device

My computer only has two USB ports, and I've plugged in my device 6 times. (removing it 5).
I can get this list to clear by restarting, but I figure there should be another way? Yesterday when I was playing around with it the number incremented when I plugged it in a second time ie ttyACM1

I try to open /dev/ttyACM0 with cutecom but it fails. I don't know if the problem is the duplication or something else. Is there a way to get rid of them?

I'm running Ubuntu 13.04 with parallels 9 on a mac.

EDIT:
Did I post this in the wrong place?

---

### Post by tjudsonesch on 2014-06-17
Well I haven't figured out the duplication problem, but it seems the reason it wouldn't open was permissions for /dev/tty

---

