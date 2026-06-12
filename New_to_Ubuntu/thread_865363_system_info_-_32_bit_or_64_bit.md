---
title: "system info - 32 bit or 64 bit?"
date: 2008-07-20
forum: New to Ubuntu
---

### Post by charles_316 on 2008-07-20
how do i check the version of Ubuntu I am running? im not sure if it is the 32 bit or 64 bit version of Hardy Heron

---

### Post by richiewrt on 2008-07-20
I could be wrong, but I believe you can run in a terminal 
```
uname -a
```

---

### Post by Yannick Le Saint kyncani on 2008-07-20
dpkg --print-architecture

---

### Post by charles_316 on 2008-07-20
charles@charles-laptop:~$ uname -a
Linux charles-laptop 2.6.24-19-generic #1 SMP Fri Jul 11 23:41:49 UTC 2008 i686 GNU/Linux

that is the output when i use ur command....

doesnt show if it is 32 or 64 bit tho :s

---

### Post by zvacet on 2008-07-20
It is 32 bit version.

---

### Post by tjwoosta on 2008-07-20
yea this is what 64bit looks like

```

tj@tj-laptop:~$ uname -a
Linux tj-laptop 2.6.24-19-generic #1 SMP Fri Jul 11 21:01:46 UTC 2008 x86_64 GNU/Linux
tj@tj-laptop:~$ 

```

---

### Post by richiewrt on 2008-07-20
i686 or i386 is 32bit and x86_64 is 64 bit.

---

### Post by dfreer on 2008-07-20
> **charles_316 said:**
> $ uname -a
Linux charles-laptop 2.6.24-19-generic #1 SMP Fri Jul 11 23:41:49 UTC 2008 **i686** GNU/Linux

The highlighted bold section means you are using a i686-optimized kernel, which is a 32-bit kernel. My AMD64 machine shows something like this:

```
$ uname -a
Linux somehost 2.6.24-1-amd64 #1 SMP Sat May 10 09:28:10 UTC 2008 **x86_64** GNU/Linux
```

You can also get the same results with a *uname -m*, FYI.

EDIT: Oh noes redundancy check error!1!

---

