---
title: "[SOLVED] Sudo Error Message"
date: 2008-11-20
forum: New to Ubuntu
---

### Post by Miljet on 2008-11-20
Every time I use sudo at the command line I get a message about unable to resolve host. It doesn't seem to cause any problems. The password input appears immediately below and everything seems to work from that point on. Just wondering what causes it.

```
 jack@jack-laptop:~$ sudo apt-get update
sudo: unable to resolve host jack-laptop
[sudo] password for jack: 

```

---

### Post by handydan918 on 2008-11-20
> **Miljet said:**
> Every time I use sudo at the command line I get a message about unable to resolve host. It doesn't seem to cause any problems. The password input appears immediately below and everything seems to work from that point on. Just wondering what causes it.

```
 jack@jack-laptop:~$ sudo apt-get update
sudo: unable to resolve host jack-laptop
[sudo] password for jack: 

```
Here is one possibility, look at your /etc/hosts file, and see if localhost and jack-laptop both have the same ip, which should be 127.0.0.1, as below in mine.
```
root@blackbox:/home/daniel# cat /etc/hosts
127.0.0.1       localhost
127.0.0.1       blackbox

```

(Relax, all you thought-police types. This isn't an Ubu system. I'm allowed to use my root account here!)

:lolflag:

---

### Post by Miljet on 2008-11-20
Never mind -- I found it. There was a discrepancy between the /etc/hosts file and the /etc/hostname files.

---

