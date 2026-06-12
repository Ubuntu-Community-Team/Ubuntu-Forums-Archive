---
title: "aclocal error"
date: 2011-11-25
forum: New to Ubuntu
---

### Post by mayur.purohit on 2011-11-25
Hi,
I am trying to run the ./autogen.sh command in Ubuntu 64 bit server and it shows the error : {./autogen.sh: 6: aclocal: not found} . The same command works on Ubuntu 32 bit server.
 
kindly help.

---

### Post by lechien73 on 2011-11-25
Hi & welcome to the forums,

aclocal is part of the automake package. Do you have it installed?

Try:

```
sudo apt-get install automake
```

---

