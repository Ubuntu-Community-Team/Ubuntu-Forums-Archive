---
title: "FF closes unexpected"
date: 2008-06-14
forum: New to Ubuntu
---

### Post by benste on 2008-06-14
hy,
my firefox closes from time to time (using FF3)
but I'm not shure why - can you help me?
I started some things in the folowing thread, but it was offtopic

[http://ubuntuforums.org/showthread.php?t=774091&page=2]("http://ubuntuforums.org/showthread.php?t=774091&page=2")

---

### Post by prshah on 2008-06-14
> **benste said:**
> hy,
my firefox closes from time to time (using FF3)
but I'm not shure why - can you help me?



The next time it closes down, open a terminal (Applications-Accessories-Terminal), then give the following commands and post the output here.
```
dmesg | tail
```

---

### Post by benste on 2008-06-14
here it is (closed gmail while regarding ubuntuforums)
```
benste@vaiofe31m:~$ dmesg | tail
[  105.996602] CPU0 attaching NULL sched-domain.
[  105.996609] CPU1 attaching NULL sched-domain.
[  106.010134] CPU0 attaching sched-domain:
[  106.010141]  domain 0: span 03
[  106.010144]   groups: 01 02
[  106.010153] CPU1 attaching sched-domain:
[  106.010156]  domain 0: span 03
[  106.010159]   groups: 02 01
[  122.457946] wlan0: no IPv6 routers present
[  142.453267] process `skype' is using obsolete setsockopt SO_BSDCOMPAT

```

---

### Post by benste on 2008-06-14
seems to handle skype CPu and WLan

I'm using a C2D T5600 with 1.86 ghz
a intel wirelss chipset (ipw ... not N series) (I'm connceted via wlan)
skype: V 2.0.0.68 - error is reproducable without an opened skype

---

### Post by llamakc on 2008-06-14
FF3 and Flash don't play well together. Are flash videos or content on sites the common denominator?

---

### Post by prshah on 2008-06-15
> **benste said:**
> 
```
benste@vaiofe31m:~$ dmesg | tail
[  105.996602] CPU0 attaching NULL sched-domain.
[  105.996609] CPU1 attaching NULL sched-domain.

```

> **llamakc said:**
> FF3 and Flash don't play well together. Are flash videos or content on sites the common denominator?

Your dmesg looks fine (irrelevant to the issue at hand), so I suspect llamakc is more on the track.

---

### Post by benste on 2008-06-16
But there is no flash part in both sites !!

---

