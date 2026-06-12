---
title: "scripting help"
date: 2013-09-16
forum: New to Ubuntu
---

### Post by rburkartjo on 2013-09-16
doing something wrong here is script to clear cache. where xxx is my password

#!/bin/bash
echo xxx | sudo -S sync; sudo echo 3 > /proc/sys/vm/drop_caches
if i open a terminal and type ./clearcache(the scripts name) i get this error

ray@ray-Latitude-D630:~$ ./clearcache
[sudo] password for ray: ./clearcache: line 2: /proc/sys/vm/drop_caches: Permission denied
 
however if u change to root it works
ay@ray-Latitude-D630:~$ sudo su
root@ray-Latitude-D630:/home/ray# ./clearcache
root@ray-Latitude-D630:/home/ray# 
tks

---

### Post by steeldriver on 2013-09-16
```
sudo echo 3 > /proc/sys/vm/drop_caches
```

applies sudo to the echo (which doesn't need it) but not to the stream redirection > /proc/sys/vm/drop_caches (which does) - you can do either

```
echo 3 | sudo tee /proc/sys/vm/drop_caches
```

or

```
sudo sh -c "echo 3 > /proc/sys/vm/drop_caches"
```

however really the best solution is to run the whole script with sudo instead of having individual sudos inside it - especially not a good idea to have your sudo password in plain text inside a file - if it really needs to run without manual input then create a NOPASSWD entry for the script in your sudo config.

---

### Post by rburkartjo on 2013-09-16
steel tks for the answer and advise

---

