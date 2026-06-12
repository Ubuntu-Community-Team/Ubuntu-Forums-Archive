---
title: "Ubuntu will not start. Input/output error. libpthread.so.0."
date: 2012-01-11
forum: New to Ubuntu
---

### Post by deckerry on 2012-01-11
Has anybody seen this one before?

```
/sbin/init: error while loading shared libraries: libpthread.so.0: cannot open shared object file: Input/output error
```It is preventing my computer from starting.

I have Ubuntu Studio 11.04 (64bit). I have no idea what caused this. It was working fine before I shut it off. Now it won't do anything.

Please,  almighty Forum Gods, share with me your never-ending wisdom. Amen.

---

### Post by adityamagadi on 2012-01-11
try booting in as a live session user through ur installation cd n run sudo apt-get install -f. 
or try the same cmd if u r able to open a cmd prompt

---

### Post by deckerry on 2012-01-12
Nothing seemed to happen.

Mr. Terminal said:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

---

### Post by adityamagadi on 2012-01-13
then you might consider re-installing ubuntu :D

---

### Post by deckerry on 2012-01-14
Reinstalling, to me, is like giving up.

BUT

That is, unfortunately, what I have decided to do.

And, of course, my computer works again.

I wouldn't consider this a "solved" case because the problem was never actually solved but it is a closed case, nevertheless.

Thanks everybody who helped!

---

