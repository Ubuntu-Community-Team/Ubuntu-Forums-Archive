---
title: "Brasero doesnt burn DVD's"
date: 2008-05-22
forum: New to Ubuntu
---

### Post by metasolaris on 2008-05-22
Hi,

Tried to burn to a DVD RAM but Brasero says I dont have the right plugins to do it!?

Thanks
meta

---

### Post by metasolaris on 2008-05-22
Just installed K3b and that wont burn either - asks me to insert a blank DVD RW when the DVD RAM is in drive...!?

---

### Post by iaculallad on 2008-05-22
Had you tried using the terminal growisofs command if it works?

growisofs -speed=1 -dvd-compat -Z /dev/your_dvd_drive -dvd-video /(place your file path and name in here)

Or had you tried to run k3b using root?

---

