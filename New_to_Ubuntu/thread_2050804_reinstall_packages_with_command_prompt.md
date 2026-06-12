---
title: "reinstall packages with command prompt?"
date: 2012-08-31
forum: New to Ubuntu
---

### Post by Paco62 on 2012-08-31
using ubuntu 10.04     synaptic gives the option to reinstall packages, is it also possible to do this with a command prompt?

---

### Post by steeldriver on 2012-08-31
well there's 

```
sudo apt-get install --reinstall *package*
```or if you want to reinstall config files as well you could do

```
sudo apt-get purge *package*
sudo apt-get install *package*
```

---

