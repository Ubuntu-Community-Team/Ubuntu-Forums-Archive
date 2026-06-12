---
title: "setting up a second user"
date: 2008-05-06
forum: New to Ubuntu
---

### Post by zenmamajen on 2008-05-06
Couldn't find this anywhere!

During Ubuntu 7.10 installation I was asked to set up additional users.

This was not asked during Kubuntu 8.04 installation and I can't find how to do it.

---

### Post by tamoneya on 2008-05-06
```
sudo mkdir /home/username
sudo useradd username
```

---

### Post by zenmamajen on 2008-05-06
awesome thanks :) now how do I give him a password?

---

### Post by tamoneya on 2008-05-06
```
sudo passwd username
```

---

