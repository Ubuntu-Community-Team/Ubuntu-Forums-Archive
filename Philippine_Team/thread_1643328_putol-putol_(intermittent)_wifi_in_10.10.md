---
title: "putol-putol (intermittent) wifi in 10.10"
date: 2010-12-11
forum: Philippine Team
---

### Post by jepong on 2010-12-11
Decided to go full time again on Linux. 

Anyone experiencing the same (shoutout to rene orense, pareho tayo ng laptop)? Its not my router since ok naman sa windows at sa iphone ko. so i think its within the OS na or the NM.

I'm using a Atheros Communications Inc. AR9285 Wireless Network Adapter.

---

### Post by pinoyskull on 2010-12-13
post the logs here, it would help us debug the problem :)

---

### Post by killer_d76 on 2010-12-13
have you already tried WICD?

---

### Post by jepong on 2010-12-13
> **pinoyskull said:**
> post the logs here, it would help us debug the problem :)

ano information kailangan mo vlad?

bigla na ddrop yung wifi connection eh and its a known issue na... [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/660864](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/660864)

---

### Post by jepong on 2010-12-13
> **killer_d76 said:**
> have you already tried WICD?

wicd is a nice workaround... but it's still a workaround. Pati wala pa cyang support sa mobile broadband, medyo heavy user ako ng globe tattoo.

---

### Post by pinoyskull on 2010-12-13
Jepong,

Have you tried the upgrading the kernel approach?
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/660864/comments/9](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/660864/comments/9)

---

### Post by jepong on 2010-12-13
di pa but i'm getting there... header and image, right?

---

### Post by jepong on 2010-12-24
installing linux-backports-modules-wireless-maverick-generic does the trick!

---

