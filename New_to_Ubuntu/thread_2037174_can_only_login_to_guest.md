---
title: "can only login to guest"
date: 2012-08-03
forum: New to Ubuntu
---

### Post by z3nhakr on 2012-08-03
i uninstalled then reinstall the fglrx drivers. now when ever i try to login it takes me back to the login screen. but guest still works. HELP?

---

### Post by NikTh on 2012-08-03
Hi ,
please open a terminal and post the output of 

```
ls -l /home/username/.Xauthority
``` 

username = your username from corrupted account. 

Thanks

---

### Post by z3nhakr on 2012-08-03
```
-rw------- 1 root root 51 Jul 31 10:42 /home/z3n/.Xauthority
```

---

### Post by steeldriver on 2012-08-03
I think where NikTh is going with this is that the file should be owned by you - if it becomes root-owned the easiest fix is to delete it

```
sudo rm /home/z3n/.Xauthority
```A new file (with the right ownership) will be created when you log in to the X session

---

### Post by z3nhakr on 2012-08-03
thanks that worked :D

---

### Post by NikTh on 2012-08-03
Hi ,
@steeldriver caught up . :) 

Glad it worked. 

Thanks

---

