---
title: "get rid of Ubuntu one"
date: 2013-07-01
forum: New to Ubuntu
---

### Post by ub9876 on 2013-07-01
how do you Really delete this thing totally and for good??13.04

---

### Post by NikTh on 2013-07-01
Open a terminal (CTRL+ALT+T) and issue the following command 

```
sudo apt-get -s purge ubuntuone-*
``` 

Above command is a simulation of the real command (without -s). See what packages will be removed and if you are OK, then proceed to the real command (without -s) 

Regards
 NikTh

---

### Post by ub9876 on 2013-07-01
????????????

---

### Post by houseworkshy on 2013-07-01
The "-s" is a switch for the command which means "simulate".  If you open a terminal and type "man apt-get" you will see the manual page for the "apt-get" command which gives you more details.  I think that NikTh is suggesting that you have a look at what will be removed first just in case other things you may want to keep are tied in with it.

---

