---
title: "[SOLVED] ssh login ?"
date: 2008-08-23
forum: New to Ubuntu
---

### Post by garyed on 2008-08-23
What am I missing?
I can login to my computers tied to my router using the ip no. but I can't if I use the computer name.

```
 ssh gary@192.168.1.101 
```
gets me in to computer host name " music-desktop "
but:
```
 ssh gary@music-desktop 
```
returns : name or service not known

---

### Post by AndyCooll on 2008-08-23
That's because your pc doesn't know the IP address of music-desktop.

You'd need to edit you /etc/hosts file to do that and add the IP address and name of the other pc.

:cool:

---

### Post by garyed on 2008-08-23
> **AndyCooll said:**
> That's because your pc doesn't know the IP address of music-desktop.

You'd need to edit you /etc/hosts file to do that and add the IP address and name of the other pc.

:cool:

Thanks,

That did the trick

---

