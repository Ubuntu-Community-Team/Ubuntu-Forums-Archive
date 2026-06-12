---
title: "error a couple of seconds into installing"
date: 2012-09-23
forum: New to Ubuntu
---

### Post by gvpj on 2012-09-23
may i know what this means:

[[img]http://s19.postimage.org/6k6difkan/2012ubu_015.jpg[/img]](http://postimage.org/image/6k6difkan/)

---

### Post by sandyd on 2012-09-23
What version of Ubuntu are you trying to install?

---

### Post by daslinkard on 2012-09-23
Probably going to 12.04 if I had to guess....the panic 0x91/0x1 was a known bug with the powernap....though I am not for sure if this has been fixed yet?

---

### Post by sandyd on 2012-09-23
> **daslinkard said:**
> Probably going to 12.04 if I had to guess....the panic 0x91/0x1 was a known bug with the powernap....though I am not for sure if this has been fixed yet?

It has not been fixed.

With that, I would suggest to try Comment #5 in [https://bugs.launchpad.net/ubuntu/+source/powernap/+bug/990146](https://bugs.launchpad.net/ubuntu/+source/powernap/+bug/990146)

---

### Post by gvpj on 2012-09-23
> **sandyd said:**
> What version of Ubuntu are you trying to install?
The one on ubuntu.com front page it says - Ubuntu 12.04.1 LTS

---

### Post by daslinkard on 2012-09-23
As pointed out by sandyd, this is still a known bug.[[COLOR=#DD4814]****[/COLOR]]("http://ubuntuforums.org/member.php?u=717412")

---

### Post by gvpj on 2012-09-23
> **sandyd said:**
> It has not been fixed.

With that, I would suggest to try Comment #5 in [https://bugs.launchpad.net/ubuntu/+source/powernap/+bug/990146](https://bugs.launchpad.net/ubuntu/+source/powernap/+bug/990146)

Comment no.5 says:
**Check in /etc/pm/power.d/01cpu_online does not have executable bit, and if it does, then just remove it. That should stop offlining CPus and you should not see this issue anymore.**

Is there a step by step newbie guide to doing this?

Also is the bug in the 32 bit version too? The error I get is during a 64 bit version install.

---

### Post by sandyd on 2012-09-24
```

sudo chmod -x /etc/pm/power.d/01cpu_online

```

---

