---
title: "How do I know if I have 32 bit or 64 bit ubuntu?"
date: 2011-12-20
forum: New to Ubuntu
---

### Post by tc101 on 2011-12-20
How do I know if I have 32 bit or 64 bit ubuntu?  I am running 10.04.

---

### Post by howefield on 2011-12-20
Try uname -a in a terminal.

If you have x86_64 in the output you are running 64 bit.

uname -m will tell you also.

---

### Post by tc101 on 2011-12-20
It says:

tom@tom-desktop:~$ uname -a
Linux tom-desktop 2.6.32-37-generic-pae #81-Ubuntu SMP Fri Dec 2 22:24:22 UTC 2011 i686 GNU/Linux

So I assume that means 32bit.  Correct?

---

### Post by howefield on 2011-12-20
> **tc101 said:**
> So I assume that means 32bit.  Correct?

Yes :-)

---

### Post by d2btoo on 2011-12-20
Yes! i686 is 32 bit.

*oops posted at same time*

---

### Post by dFlyer on 2011-12-20
Your running the 32bit version with the pae kernel which will use 4gig of memory if you have it.

---

### Post by bemo18 on 2012-10-13
enter uname -m in terminal. if the output is x86_64 it is a 64-bit. If the output is i686 it is 32-bit

---

### Post by NikTh on 2012-10-13
And another way ```
lscpu | grep Arch
```

---

