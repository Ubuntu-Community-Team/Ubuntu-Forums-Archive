---
title: "[SOLVED] a problem on update"
date: 2008-06-14
forum: New to Ubuntu
---

### Post by rhanex on 2008-06-14
Fetched 216kB in 0s (246kB/s)
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 



**whats that means??**

---

### Post by Rocket2DMn on 2008-06-14
Open a terminal from Applications->Accessories->Terminal and run
```
sudo dpkg --configure -a
```
Then you can continue with what you were doing.

---

### Post by st33med on 2008-06-14
Run in the terminal:
```
sudo dpkg --configure -a
```

---

### Post by Sef on 2008-06-14
> Fetched 216kB in 0s (246kB/s)
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.



whats that means??

It reconfigures all of the [unpacked]("http://webopedia.internet.com/TERM/U/unpack.html") downloads.

---

### Post by rhanex on 2008-06-18
**SOLVED**
thanks guys and also for the info,love my new os ;);)

---

