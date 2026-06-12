---
title: "how to check what video card you have"
date: 2008-06-28
forum: New to Ubuntu
---

### Post by bu2971x on 2008-06-28
how to do this from terminal...thanks

---

### Post by PmDematagoda on 2008-06-28
```
lshw -C video
```
should do it.

---

### Post by ibutho on 2008-06-28
Another is 
```
sudo lspci | grep -i vga
```
Thats helpful if you happen to run a distro that does not include lshw by default.

---

### Post by esbo on 2008-06-28
If you have windows as wel there are several hardware info utilites, such as
Sisoft Sandra and AIDA32 which will also sort of stuff about your hardware.

---

### Post by bondo101 on 2008-07-27
Where do you download sisoft sandra for linux please help and thankyou
                                                       bondo101

---

### Post by seagullplayer77 on 2008-07-27
There isn't a version of SiSoft Sandra for Linux, as far as I can tell. I'm almost certain it's a Windows tool: 

[http://mandrivausers.org/index.php?showtopic=19439](http://mandrivausers.org/index.php?showtopic=19439)

---

