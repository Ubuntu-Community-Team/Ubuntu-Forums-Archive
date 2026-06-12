---
title: "[SOLVED] relocating home folder. Does anyone know how"
date: 2008-11-24
forum: New to Ubuntu
---

### Post by nakama85 on 2008-11-24
I have 2 Hard drives

1 has ubuntu on it with no partitions for home or swap

the other I just partitioned with ext3 and swap

How do I tell ubuntu to use the new hard drive for home and swap? Note: I just Figured out how to point to swap but still cant figure out Home)
Thanks

---

### Post by jemate18 on 2008-11-24
> **nakama85 said:**
> I have 2 Hard drives

I has ubuntu on it with no partitions for home or swap

the other I just partitioned with ext3 and swap

How do I tell ubuntu to use the new hard drive for home and swap? Note: I just Figured out how to point to swap but still cant figure out Home)
Thanks


You have to edit /etc/fstab and change/add entries about what you want to be mounted.

---

### Post by jemate18 on 2008-11-24
maybe this will explain a little bit

> [http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

---

### Post by laffinet on 2008-11-24
Might not be exactly the same thing, but should help nonetheless:

[http://www.psychocats.net/ubuntu/separatehome]("http://www.psychocats.net/ubuntu/separatehome")

---

### Post by nakama85 on 2008-11-25
> **laffinet said:**
> Might not be exactly the same thing, but should help nonetheless:

[http://www.psychocats.net/ubuntu/separatehome]("http://www.psychocats.net/ubuntu/separatehome")

Thanks

This Was exactly What I was looking for.

However in following this tutorial, I found this To be pretty advanced and not very newb friendly. This tutorial was semi successful for me. I am sure if I was more experienced it would have fixed everything.

In the end I just reinstalled Ubuntu After backing up my files.

---

