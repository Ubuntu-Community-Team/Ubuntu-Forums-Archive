---
title: "PURGE Cinelerra"
date: 2013-08-01
forum: New to Ubuntu
---

### Post by czgirb on 2013-08-01
Today I'm about to purger Cinelerra

> 
czgirb@czgirb:~$ sudo apt-get purge cinelerra
[sudo] password for czgirb: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Virtual packages like 'cinelerra' can't be removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
czgirb@czgirb:~$ 


Any idea?

---

### Post by kostkon on 2013-08-01
First, try giving
```
apt-cache policy cinelerra-cv
```

---

### Post by slickymaster on 2013-08-01
> **czgirb said:**
> Today I'm about to purger Cinelerra

Any idea?
```
sudo apt-get purge cinelerra\*
```should do it.

---

### Post by czgirb on 2013-08-01
> **slickymaster said:**
> ```
sudo apt-get purge cinelerra\*
```should do it.

Yup! It's done.
But please tell me
> sudo apt-get purge cinelerra
won't do it? and why
> sudo apt-get purge cinelerra\*
should do it?
What is > \* for?
Please guide me ...

---

