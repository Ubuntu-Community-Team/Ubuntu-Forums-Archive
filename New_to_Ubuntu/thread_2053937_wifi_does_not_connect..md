---
title: "wifi does not connect."
date: 2012-09-06
forum: New to Ubuntu
---

### Post by cosmoshell on 2012-09-06
lspci |grep "Network"

03 00 0 network controller  Intel Corperation Centerino Wireless-N + WiMAX 6150 ( rev 67).

finds SSID but when i connect it gets stuck at obtaining IP address.

---

### Post by blazemore on 2012-09-06
Does the network you're connecting to have a password?

If so, were you asked for the password?

---

### Post by cosmoshell on 2012-09-06
> **blazemore said:**
> Does the network you're connecting to have a password?

If so, were you asked for the password?

no password. no encryption.

---

### Post by cosmoshell on 2012-09-08
wifi still doesent connect.

---

### Post by blazemore on 2012-09-10
What happens if you try to obtain an IP address manually

---

### Post by Cpierce on 2012-09-10
Had the same problem with a WiMax 6050. I googled and found the driver and installed it manually, then it worked as it should.

---

### Post by cosmoshell on 2012-09-11
is there a modprobe thingy for this?
what kernal-backports should i try?

also static ip settings dont change anything, tried multiple things in wicd even deleted its configs.

---

### Post by cosmoshell on 2012-09-15
> **cosmoshell said:**
> lspci |grep "Network"

03 00 0 network controller  Intel Corperation Centerino Wireless-N + WiMAX 6150 ( rev 67).

finds SSID but when i connect it gets stuck at obtaining IP address.

I am also useing wicd, in icewm. this issue doesn't accor in gnome. any new suggestions?

---

