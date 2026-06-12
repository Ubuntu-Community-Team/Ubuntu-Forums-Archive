---
title: "Driver that depends on USB controller ?"
date: 2007-02-09
forum: Programming Talk
---

### Post by rralijaona on 2007-02-09
Hello,

Using libusb, I've written a driver for a USB Digital scope.

But there's a very strange thing that I noticed : the driver works *only with some USB controllers*, but not with others!

* Communication with the scope work correctly :
1. D-Link DUB-H7
2. The Hub integrated in my DELL screen
3. Belkin F5U219 PCI (rev 4)
        
* No communication available with the scope :
4. SiS USB controller (rev 0F) (in the 2 AMD64, and the last P4)
5. D-Link DU-520 (rev A1) (PCI)


If I plug an USB key, it is correctly seen on all of them, and I can correctly read/write whatever I want. That means that the USB controller works fine.
But the communications work correctly ONLY with the 3 first USB controllers.

And with the 4th and 5th USB controller, if I ever plug the D-Link DUB-H7, and then plug the scope in the hub, communications will work.

So, it seems that there is something really linked to the USB controllers.


Does someone know any reason that may lock my communications when using these USB controllers?



Thanks in advance

---

