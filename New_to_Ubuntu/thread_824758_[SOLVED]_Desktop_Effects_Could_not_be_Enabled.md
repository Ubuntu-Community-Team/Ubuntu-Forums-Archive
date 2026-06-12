---
title: "[SOLVED] Desktop Effects Could not be Enabled"
date: 2008-06-10
forum: New to Ubuntu
---

### Post by balachandarlinks on 2008-06-10
I m using** Ubuntu Hardy**...I **fully updated** the system..I m using **intel motherboard with inbuilt graphics memory**.....

  My system gives all desktop effects fine....But one time i installes compiz window manager and change my window manager to **metacity** and then i change it to **compiz** ....
 
  After that my desktop effects couldnt be enabled....I m gr8 fan of this effects.....

 ** Please Help me...**

---

### Post by Inxsible on 2008-06-10
Press Alt + F2 and type in ```
compiz --replace
```See if that enables compiz

---

### Post by balachandarlinks on 2008-06-10
No after that too i got the same message...**Desktop effects could not be enabled....**

---

### Post by adityakavoor on 2008-06-10
try this once

```
sudo dpkg-reconfigure xserver-xorg
```

and then enable compiz

---

### Post by balachandarlinks on 2008-06-10
I fix it myself....I put loose bindings option in compiz and get back my effects............:popcorn::lolflag:

---

### Post by adityakavoor on 2008-06-10
mark the thread as solved

---

