---
title: "$Display yields nothing"
date: 2008-06-09
forum: New to Ubuntu
---

### Post by spanish07 on 2008-06-09
I read the wiki for ssh and i have xauth downloaded and my /etc/ssh/sshd_config having X11 forwarding on yes but still echo $Display gives me a big fat blank haha any suggestions?

---

### Post by Nepherte on 2008-06-09
You have to give $Display a value first:
```
export Display=somevalue
```
I'm not sure what value though.

---

### Post by Slim Odds on 2008-06-09
For X, it's DISPLAY   (all caps)

---

