---
title: "Bass/Treble settings in Ubuntu 12.04?"
date: 2012-08-09
forum: New to Ubuntu
---

### Post by Houmie on 2012-08-09
Hi,

My Bass is set to highest bar (Digital Output (S-PDIF)) and I have found no way to lower it in Ubuntu.

Any tips?


Many Thanks,

---

### Post by acimi66 on 2012-08-09
using command line:

alsamixer

Good luck

---

### Post by Houmie on 2012-08-10
Ahhh this is awesome. Thank you so much !!! :guitar:

---

### Post by Houmie on 2012-09-08
> **acimi66 said:**
> using command line:

alsamixer

Good luck

There is a problem. Everytime I reboot the PC, I loose my settings.  Is there a way to persist the values for alsamixer?

Thank you

---

### Post by ebirah on 2012-12-18
sudo alsactl store

---

