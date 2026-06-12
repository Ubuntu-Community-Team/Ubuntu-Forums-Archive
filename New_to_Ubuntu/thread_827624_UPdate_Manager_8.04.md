---
title: "UPdate Manager 8.04"
date: 2008-06-12
forum: New to Ubuntu
---

### Post by Gember on 2008-06-12
Dear Sir,

I am looking your help. I have updated ubunto 8.04 as I recommended by the update manager. Last time update changes the kernel from that time on any upgrade get freeze. what do I have to do? any help?

Genber

---

### Post by Xiong Chiamiov on 2008-06-12
Can you please run
```

sudo aptitude update

```
then post the results of
```

sudo aptitude safe-upgrade

```
?  (These are terminal commands, by the way; get to the terminal from Applications -> System Tools)

---

### Post by Gember on 2008-06-13
Thank you for advise.

Updates are installed but the update manager still freezes? any suggestion?

Gember

---

### Post by Xiong Chiamiov on 2008-06-13
If you try to install things using apt-get or aptitude, does that work?  If they do, then it's just a problem with Synaptic, rather than with the whole installation process.

---

