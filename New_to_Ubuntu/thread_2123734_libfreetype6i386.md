---
title: "libfreetype6/:i386"
date: 2013-03-08
forum: New to Ubuntu
---

### Post by 18cwatford on 2013-03-08
For some reason I cannot update anything, install anything or remove anything, that is in the software center, via gui or terminal, because I keep getting the following error;

```

 libfreetype6 : Breaks: libfreetype6:i386 (!= 2.4.8-1ubuntu2.1) but 2.4.8-1ubuntu2 is to be installed
 libfreetype6:i386 : Breaks: libfreetype6 (!= 2.4.8-1ubuntu2) but 2.4.8-1ubuntu2.1 is to be installed

```

I've tried sudo apt-get -f install
I've tried to remove libfreetype
I've tride to my limits but I can't seem to fix it.

Also judging by "i386" this could or couldn't be related to 64 bit, noted that I running one.

---

### Post by schragge on 2013-03-17
Try to remove the foreign arch package with dpkg:
```
dpkg -r libfreetype6:i386
```

---

