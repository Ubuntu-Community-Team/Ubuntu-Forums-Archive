---
title: "Connect to Serial"
date: 2015-07-26
forum: New to Ubuntu
---

### Post by shaunnevi on 2015-07-26
Hello Guys

I am new to Xubuntu.I want to connect via serial to usb cable to a devices serial port.
I am not sure how to begin.What commands should be using please.

Thanks
DD

---

### Post by sandyd on 2015-07-26
Hi, can you post the output of the following commands
```

lsusb
sudo setserial -g /dev/ttyS[0123]

```
The first command will show all your USB devices, while the second will list your serial ports.

---

