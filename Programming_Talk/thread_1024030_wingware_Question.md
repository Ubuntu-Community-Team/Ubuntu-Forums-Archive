---
title: "wingware Question"
date: 2008-12-28
forum: Programming Talk
---

### Post by perlsyntax on 2008-12-28
How do i install the wingware on linux i am try to install the free.I did download the deb file but i not sure how to start it?

---

### Post by thornmastr on 2008-12-28
> **perlsyntax said:**
> How do i install the wingware on linux i am try to install the free.I did download the deb file but i not sure how to start it?

Does this help?

[http://www.cyberciti.biz/faq/ubuntu-linux-how-do-i-install-deb-packages/](http://www.cyberciti.biz/faq/ubuntu-linux-how-do-i-install-deb-packages/)

Robert

---

### Post by Ahadiel on 2008-12-28
You can either double-click it, or
```
dpkg -i /path/to/file.deb
```

---

### Post by perlsyntax on 2008-12-28
root@perlsyntax-desktop:~# dpkg -i wingide3.1_3.1.6-1_i386.deb
Selecting previously deselected package wingide3.1.
(Reading database ... 121337 files and directories currently installed.)
Unpacking wingide3.1 (from wingide3.1_3.1.6-1_i386.deb) ...
dpkg: dependency problems prevent configuration of wingide3.1:
 wingide3.1 depends on enscript (>= 1.6.1-1); however:
  Package enscript is not installed.
dpkg: error processing wingide3.1 (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 wingide3.1


i did that deb -i file name and i got this.And how do i get it to run?

---

### Post by Ahadiel on 2008-12-28
Ah yes, I forgot dpkg doesn't have dependancy resolution. You could try using gdebi
```
gdebi /path/to/file.deb
```

---

