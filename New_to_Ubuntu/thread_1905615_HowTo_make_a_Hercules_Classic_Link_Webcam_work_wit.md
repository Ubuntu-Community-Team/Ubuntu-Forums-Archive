---
title: "HowTo make a Hercules Classic Link Webcam work with 11.10"
date: 2012-01-07
forum: New to Ubuntu
---

### Post by Stefano1970 on 2012-01-07
Hallo,

I have an old Compaq Presario laptop running Ubuntu 11.10:
I'm looking for a driver for my new webcam Hercules Classic Link version  3.2. I just got a CD with the driver for Windows.
Anyone could help me?
Thanks a lot.

Stefano :sad:

---

### Post by lechien73 on 2012-01-07
I remember from before that this webcam suffers from compatibility issues with Ubuntu. Could you plug the camera in and then run:

```
lsusb
```

Please post the output here, wrapped with CODE tags (the **#** button on the toolbar).

Thanks

---

### Post by Stefano1970 on 2012-01-07
This is the output:
```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 003: ID 06f8:3009 Guillemot Corp. 
```Thanks a lot.

---

### Post by lechien73 on 2012-01-07
Hmmmm...I could be mistaken, but your only option may be to replace the camera. I looked up some information regarding the Hercules, and the hacked driver doesn't work for it: [http://www.rastageeks.org/ov51x-jpeg/index.php/Working_Webcams](http://www.rastageeks.org/ov51x-jpeg/index.php/Working_Webcams)

As you will see, the Guillemot Corp webcam with the same ID as yours is listed as not working!

I'll keep looking to see if I can find anything else, but a webcam, such as a Logitech that supports V4L might be the only way to go.

---

### Post by Stefano1970 on 2012-01-07
Thank you for your answer.

Stefano

---

