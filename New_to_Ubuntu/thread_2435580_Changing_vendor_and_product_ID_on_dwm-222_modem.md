---
title: "Changing vendor and product ID on dwm-222 modem"
date: 2020-01-22
forum: New to Ubuntu
---

### Post by bassmonster on 2020-01-22
Hello all,
As per the title, I would like to know if there is a way to change the vendor and product ID on the DLink dwm-222 modem.

I'm setting up a watchgaurd firebox with the modem as  4G failover just in case if the main Internet line goes down.  Watchgaurd, for whatever reason only allow this limited modem to be installed on their firebox with Vendor ID (VID) 0x0BDB and Product ID (PID) 0x1926.  However, so bar out of the 2 modems that I've purchased, the vendor and product ID are different which is leading to the failure of modem detection on the firebox.

Please be gentle as I'm new to Ubuntu and may have a lot of silly questions. 

Any help and advice would be greatly appreciated.

---

### Post by CelticWarrior on 2020-01-22
Welcome :)

The question is not silly but hardly anything to do with Ubuntu.
And the answer is no, you can't do that, because that information is coded in the product's firmware. Changing it would require flashing a different and probably incompatible firmware. It would result in bricking the device.

---

