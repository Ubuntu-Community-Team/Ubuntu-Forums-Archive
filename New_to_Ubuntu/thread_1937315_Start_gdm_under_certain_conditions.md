---
title: "Start gdm under certain conditions"
date: 2012-03-07
forum: New to Ubuntu
---

### Post by Chiel92 on 2012-03-07
Hi,

I want to be able to boot into text-only mode, but only under certain circumstances, for example when I press a certain key.
I initially thought to change the runlevel. Because Ubuntu works with upstart nowadays, it took me quite some time to figure out how to prevent gdm not to start on runlevel 3.
I got that working, such that when I change
```
       env DEFAULT_RUNLEVEL=2

```into 
```
       env DEFAULT_RUNLEVEL=3

``` (in /etc/init/rc-sysinit.conf) the system will boot into text-only.

Now I only need to be able to capture a key (i.e. reading the keystatus) while booting, such that gdm will not start when pressed a certain key. However, I don't know how and where to do that.

Any suggestions? Thanks in advance!

Regards

---

### Post by Chiel92 on 2012-03-08
bump

---

