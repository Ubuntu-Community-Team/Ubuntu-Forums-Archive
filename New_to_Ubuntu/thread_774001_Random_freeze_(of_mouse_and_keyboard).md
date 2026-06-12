---
title: "Random freeze (of mouse and keyboard?)"
date: 2008-04-29
forum: New to Ubuntu
---

### Post by zephyrkz on 2008-04-29
Hi.  I am an absolute newbie in ubuntu or linux, and I just took a shot at installing ubuntu 8.04. In live CD, ubuntu freezes randomly in less than 5-10 min. Note that I have had same problem in previous version gutsy (in which I tried everything I could, installing with different version, using alternate CD, etc.), which made me gave up on ubuntu until the new version came out. 

My machine runs AMD64 and nvidia 8600GT, two hard disk (one SATA -primary, the other IDE - secondary).

Please help me out! Thx!

---

### Post by hermes0710 on 2008-04-29
In folder /var/log/ there must be a file with name Xorg.0.log or something like this. Post the contents of this file here. To see the contents execute this command from a terminal:

```
cat /var/log/Xorg.0.log
```

If it complains that the file doesn't exist try to find the correct file name in that folder that looks like this. (To open a terminal, pres <alt>+F2 and insert "gnome-terminal".

---

