---
title: "Dogecoin Wallet Won't Load After Ubuntu Upgrade"
date: 2014-02-11
forum: New to Ubuntu
---

### Post by bshatt1987 on 2014-02-11
Hi, I upgraded to 13.10 yesterday and now I can't get my Dogecoin Wallet to load.  :c
I get this error when I try to run dogecoin-qt :
"error while loading shared libraries: libboost_system.so.1.49.0: cannot open shared object file: No such file or directory"

---

### Post by ubudog on 2014-02-11
Hi,

Try installing libboost:
```
sudo apt-get install libboost1.49-all-dev libboost-system1.49-dev libboost-system1.49.0
```

---

### Post by bshatt1987 on 2014-02-11
Ha!  That did it, thank you!

---

### Post by ubudog on 2014-02-11
> **bshatt1987 said:**
> Ha!  That did it, thank you!

Glad it worked!

---

