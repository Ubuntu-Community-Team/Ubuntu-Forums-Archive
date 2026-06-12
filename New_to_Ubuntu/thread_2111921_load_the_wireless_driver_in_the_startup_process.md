---
title: "load the wireless driver in the startup process"
date: 2013-02-03
forum: New to Ubuntu
---

### Post by herbert tamayo on 2013-02-03
hi, my ubuntu 12.04 at startup process is always looking for a wired network connection trough eth0 card, this process takes like 3 minutes, at this time my wireless card is not up and running, so, if I don't have plug my network cable i have to wait this seek process, then the X is loaded and my wireless card is up (bcm43xx module)

so, i would like to load the bmc43xx module at startup problem and get rid off the 3 minutes of waiting, my question is: how can I do that??

regards

---

### Post by Yellow Pasque on 2013-02-03
I'm not sure if it will solve the issue, but you can put the name of whatever module you want to load in /etc/modules:
```
gksu gedit /etc/modules
```

---

