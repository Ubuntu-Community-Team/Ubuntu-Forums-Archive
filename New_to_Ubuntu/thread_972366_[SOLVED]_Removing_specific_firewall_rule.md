---
title: "[SOLVED] Removing specific firewall rule"
date: 2008-11-05
forum: New to Ubuntu
---

### Post by niiklas on 2008-11-05
Hello. I want to know how to remove this rule from my firewall:

```
22:tcp                     ALLOW   192.168.0.2
```

tried everything i could think of..

---

### Post by niiklas on 2008-11-05
solved it ! :D
sudo ufw delete allow proto tcp from 192.168.0.2 to any port 22

---

### Post by jdeal on 2009-04-30
Ran into same problem.  Seems you can not just delete a port rule but must at least specify a protocol.  For example:

sudo ufw delete allow 20

Does not work.  But you can do:

sudo ufw delete allow 20/tcp

which does work.

Just thought I would add this for people looking at this thread.

---

