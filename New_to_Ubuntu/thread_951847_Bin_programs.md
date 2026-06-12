---
title: "Bin programs??"
date: 2008-10-18
forum: New to Ubuntu
---

### Post by jstocky on 2008-10-18
Guys, what does this mean?

  /usr/bin/install -c  weplab /usr/local/bin/weplab
/usr/bin/install: cannot create regular file `/usr/local/bin/weplab': Permission denied
make[1]: *** [install-binPROGRAMS] Error 1
make[1]: Leaving directory `/home/stocky/weplab-0.1.5'
make: *** [install-am] Error 2
stocky@Nick:~/weplab-0.1.5$ cd
stocky@Nick:~$ sudo apt-get install binPROGRAMS
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package binPROGRAMS
stocky@Nick:~$

---

### Post by Xiong Chiamiov on 2008-10-18
> **jstocky said:**
> Guys, what does this mean?

There are 2 different issues here.
> **jstocky said:**
> 
/usr/bin/install: cannot create regular file `/usr/local/bin/weplab': Permission denied

The previous command you should have preceeded with "[sudo]("https://wiki.ubuntu.com/RootSudo")".

> **jstocky said:**
> 
stocky@Nick:~$ sudo apt-get install binPROGRAMS
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package binPROGRAMS
stocky@Nick:~$
You're trying to install a package that is not in the repository.

---

### Post by Harisz750 on 2008-10-18
what exactly are you trying/want to do?????????

---

