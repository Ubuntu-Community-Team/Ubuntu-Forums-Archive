---
title: "[SOLVED] Video card 'enabled', but not 'in use'.  No desktop effects"
date: 2008-07-30
forum: New to Ubuntu
---

### Post by ConMan318 on 2008-07-30
On my friend's computer, Ubuntu once had everything working normally, including drivers/desktop effects.  Now, though, desktop effects cannot be enabled.  In 'hardware drivers', the driver is listed, and the box for it is checked, but the status for it says 'not in use'.

The card is a Geforce 8600 GTS.

Any suggestions?

---

### Post by tuxxy on 2008-07-30
Has he installed any other drivers like by means of Envy.

---

### Post by ConMan318 on 2008-07-30
Hah it turns out he was messing with his xorg.conf to set up dual monitors and his current xorg.conf was empty.  I restored one of his backups and everything is working.  Thanks though.

---

### Post by heatpumpcontrol on 2008-07-30
> **ConMan318 said:**
> Hah it turns out he was messing with his xorg.conf to set up dual monitors and his current xorg.conf was empty.  I restored one of his backups and everything is working.  Thanks though.

please mark as solved.. thanks

---

