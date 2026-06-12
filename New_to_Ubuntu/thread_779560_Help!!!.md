---
title: "Help!!!"
date: 2008-05-02
forum: New to Ubuntu
---

### Post by splendid on 2008-05-02
I installed a new graphics card.  My Ubuntu 7.10 system attempts to boot to GUI, and then I get a message "Please Provide Passphrases for encrypted Certificate keys.

Any ideas???  If I go into recovery mode I can get to a command prompt.  I do not remember the certificate key, but that was for my ssh server anyway.  Not sure why it would prompt me for it during bootup.  At least it never did before.

Thanks

---

### Post by splendid on 2008-05-02
any ideas???

---

### Post by seshomaru samma on 2008-05-03
which card?
maker? model?

---

### Post by splendid on 2008-05-04
Nvidia GEForce FX5500  256mb DDR

---

### Post by seshomaru samma on 2008-05-06
If the problem is related to the graphic card then run:

sudo dpkg-reconfigure xserver-xorg

but if the problem is due to SSH , I can't help you...

---

