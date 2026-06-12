---
title: "Empty screen on login in 15.10"
date: 2016-03-19
forum: New to Ubuntu
---

### Post by jt4u on 2016-03-19
On my son's login he has a completely empty screen! Not launcher or anything. On the same laptop, that I'm using now with my admin login, all appears to be normal! 

Is there a way to check the user settings/restore defaults?

I can start a terminal (right click), so I could run commands if I knew what to do. 

This is running 15.10.

---

### Post by deadflowr on 2016-03-20
To restore the defaults run:
```
dconf reset -f /org/compiz/
```
then run:
```
setsid unity
```

---

### Post by jt4u on 2016-03-20
Thanks deadflowr, it did the trick!

---

### Post by Bucky Ball on 2016-03-20
*Post(s) moved to own thread. *

---

