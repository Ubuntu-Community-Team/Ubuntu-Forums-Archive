---
title: "reformatting disc"
date: 2008-09-20
forum: New to Ubuntu
---

### Post by andrewhadyn on 2008-09-20
K.d.e has installed its new look & subsequently wiped out most of the o/s.How do I reformatt to reinstall from the supplied ubunto disc?. thank you

---

### Post by bumanie on 2008-09-20
Just install over the present partitions. Ubuntu will format the partitions if directed to. May be an idea to set up a separate /home by choosing manual at the install stage. This way, if something similar happens, all your data will be safe. If you have already done this, make sure your new installation only formats /

---

### Post by sayakb on 2008-09-20
Install **gparted**
```
sudo apt-get install gparted
```
Goto System->Administration->Partition Editor and alter the partitions from there.

NOTE: You need to boot into the LiveCD and use gparted (already installed) so that you can change your / if use wish to.

---

