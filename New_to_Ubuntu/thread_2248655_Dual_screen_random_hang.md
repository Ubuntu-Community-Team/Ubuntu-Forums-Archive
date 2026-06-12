---
title: "Dual screen random hang"
date: 2014-10-16
forum: New to Ubuntu
---

### Post by Monnom_Olivier on 2014-10-16
Hi,

I'm using Ubuntu14.04 on dual screen.
Often, it arrives that my system hangs: I can move my cursor only in one of the two screens and no other actions can be made (no keyboard, no clicks,... nothing).
The only possibility for me is to reboot.
Is someone has got this problem? Can you help me?

Regards,

Olivier
NB: I've nearly the same configuration with my laptop (+external screen) and everything is ok.

---

### Post by JazzPotato on 2014-10-16
Hi there,
have you installed graphics drivers? If so, what driver specifically?
What video card are you using?

---

### Post by glyczak on 2014-10-18
I've had a very similar issue involving Xorg.
My system specs are as follows:
Graphics: Gallium 0.4 on NVA8
Processor: AMD Phenom(tm) II X4 945 Processor × 4
RAM: 8.0 GB

Help would be appreciated.

---

### Post by Vladlenin5000 on 2014-10-18
> **glyczak said:**
> Help would be appreciated.

Please read post #2

---

### Post by tgalati4 on 2014-10-20
Look through your log files:  /var/log/Xorg.0.log and /var/log/Xorg.0.log.old

---

