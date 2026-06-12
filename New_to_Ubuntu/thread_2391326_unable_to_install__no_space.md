---
title: "unable to install  no space"
date: 2018-05-08
forum: New to Ubuntu
---

### Post by yoshiki2 on 2018-05-08
Hello. I have linux mint installed, and I am trying to install ubuntu mate, however, whenever I try to I get a message that says no space..
any Ideas?

---

### Post by cruzer001 on 2018-05-08
Hello

Please post the output of:
```
df -h
```

---

### Post by deadflowr on 2018-05-08
> **cruzer001 said:**
> Hello

Please post the output of:
```
df -h
```

also post back the results from
```
sudo parted -l
```
see what the disk layout is, currently.

Also which method of install are you trying?
There should be along side or entire disk or  encrypt +/or lvm
and something else (manual)

---

