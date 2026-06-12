---
title: "No Wireless"
date: 2013-01-21
forum: New to Ubuntu
---

### Post by Riham on 2013-01-21
I just installed Ubuntu 12.04 LTS, no wireless is detected , no wireless extensions, it just can't connect.
Can anyone help me please ? 
I would really appreciate you help ! :)

---

### Post by audiomick on 2013-01-21
People who might be able to help you will need to know what your wireless card is.

do
```
sudo lshw -c network
```

in a termainal, and post the results here.

---

### Post by cactus john on 2013-01-22
My first post..and I have no idea of what I'm doing, a complete noob in Ubuntu, and currently using 12.04.
I had the same problem and after reading numerous posts found a command that fixed my no wireless..

"ifkill unblock all"

It worked.

Don't know if this will help,  but it did for me...

---

### Post by bkratz on 2013-01-22
> **cactus john said:**
> My first post..and I have no idea of what I'm doing, a complete noob in Ubuntu, and currently using 12.04.
I had the same problem and after reading numerous posts found a command that fixed my no wireless..

"[COLOR="Red"]ifkill[/COLOR] unblock all"

It worked.

Don't know if this will help,  but it did for me...

Should have been rfkill etc.

---

### Post by cactus john on 2013-01-22
yeah, can't read my own notes without having my glasses on..

---

