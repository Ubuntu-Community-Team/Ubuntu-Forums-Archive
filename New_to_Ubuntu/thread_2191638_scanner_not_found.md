---
title: "scanner not found"
date: 2013-12-03
forum: New to Ubuntu
---

### Post by desceradoe on 2013-12-03
d/l simple scan, but get msg scanner not found. It's a cannon mg3122 all in one. printer works ok in ubuntu. Scanner works ok in windows vista. i am using a dual boot system. Saw a notice about copying    /usr/lib64/sane to /usr/lib/sane     but dont know how to use that in terminal tried it but don't work , dont know how to write the copy command.

Thanks for any help;  desceradoe

---

### Post by rburkartjo on 2013-12-03
try installing xsane. then open and see if you can scan.

---

### Post by rburkartjo on 2013-12-03
it is available in the ubuntu software center

---

### Post by jimmyh1972 on 2013-12-03
Code:
sudo -s (enter yor password to get root)

[COLOR=#000000]cp /usr/lib64/sane /usr/lib/sane (press ENTER)

that's it:-)[/COLOR]

---

