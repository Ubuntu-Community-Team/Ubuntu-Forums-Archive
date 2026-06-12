---
title: "Logout Error after installation of Nvidia Graphic Driver in 13.10"
date: 2013-12-28
forum: New to Ubuntu
---

### Post by phyothiha96 on 2013-12-28
I'm a Desktop User. Recently I was installed Nvidia Graphic Driver [GeForce GT 520] from Additional Drivers. I did a reboot and logged in again when installation was finished. I could login without any problem. But I found logout error after installation of Nvidia Graphic Driver. I just wait a few second and then my monitor was idle. How Can I Fix this Problem?

Here are some of my specs:

```


Memory - 4GB
Processor - Intel(R) Pentium(R) Dual CPU E2180 @ 2.00GHz
Graphic - GeForce GT 520
OS - Ubuntu 13.10 64-bit


```

---

### Post by grahammechanical on 2013-12-28
You do mean logout and not shutdown or restart? I just wanted to make sure. The solution? Try a different driver. On my machine Additional Drivers lists two Nvidia 304 drivers and two Nvidia 331 drivers. Each of these two drivers has on version that is labelled as "tested" and the other as being Nvidia "updates." I guess that one is more experimental than the other.

Personally I find Nouveau works well for me on my Nvidia GT220.

Regards.

---

### Post by phyothiha96 on 2013-12-29
No, I've got an issue with logout error. In Additional Drivers tab, the lists of available Nvidia drivers including open source driver. I tried these drivers again and again but failed. When I tried with open source driver, the logout error has been fixed.

---

