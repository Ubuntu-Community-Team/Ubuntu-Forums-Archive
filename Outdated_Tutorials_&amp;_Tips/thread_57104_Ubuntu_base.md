---
title: "Ubuntu base"
date: 2005-08-15
forum: Outdated Tutorials &amp; Tips
---

### Post by vignesh on 2005-08-15
I installed Ubuntu4.10 in custom mode.(i.e) no gui.How do I add the build-essential package so I can compile c programs.Also how do I add emacs package.

---

### Post by nad on 2005-08-15
Use the dselect utility for package management. It is curses based and can be a llittle unnerving to learn, but will show you the current state of all the available packages for your installation as well as allow you to perform package management.

---

### Post by pmjdebruijn on 2005-08-15
Hi,

apt-get / apt-cache are also nice...

```
apt-cache search build-essential
apt-get install build-essential emacs
```

Besides, I high recommend using 5.04...

Regards,
Pascal de Bruijn

---

