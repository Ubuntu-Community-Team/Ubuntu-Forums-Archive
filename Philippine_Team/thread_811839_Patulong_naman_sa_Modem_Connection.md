---
title: "Patulong naman sa Modem Connection"
date: 2008-05-29
forum: Philippine Team
---

### Post by Africanne on 2008-05-29
Mga tol, ask ko lang po how to connect to the internet.Pag sa office,nagagamit ko ung Wifi. But my problem is i wanted to use the net connection in Ubuntu even at home. I'm here in Tanzania,Africa, and im using Huawei CDMA data modem (Correct me if im wrong pero parang similar to SmartBro).Nagagamit ko sa XP ung modem since naka-dual boot ako.But is there any way to use my modem with Ubuntu?

Tsalamats!:confused:

---

### Post by jeffimperial on 2008-05-29
**Kung ang ibig mong sabihin ay HUAWEI modem (CDMA phone) [STE2551] :)**

> **zammi said:**
> I think I myself found the solution. This is related to "usbserial" driver issue.
1. I inserted the usb cable and let system to load ti_usb_3410_5052...and found the ProductId(Say: 9999) and VendorId (Say 111). Them removed the usb cable.
2. Probe the usb serial this way: modprobe usbserial vendor=0x111 product=0x9999
3. Inserted the usb cable...
4. This time it didn't fire any error... when probing ti_usb_3410_5052, and created /dev/ttyUSB0 instead.

This part is over. But still my problem is not over. Now this has become a usual dial-up issue as others having...Cannot connect to internet yet...

Can anybody tell me how to automate the 2nd step above (Let system to automatically probe usbserial with correct VendorId/ProductId), when I inserted the modem cable.

---

### Post by Nessa on 2008-05-30
OT: Ang layo mo naman...

---

