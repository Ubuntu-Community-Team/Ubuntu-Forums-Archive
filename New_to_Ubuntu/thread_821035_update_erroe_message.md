---
title: "update erroe message"
date: 2008-06-06
forum: New to Ubuntu
---

### Post by furoido on 2008-06-06
Just tried to install Ubuntu updates and got this:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.



I tried typing in the terminal "dpkg --configure -a"

and got this:

andrew@andrew-desktop:~$ dpkg --configure -a
dpkg: requested operation requires superuser privilege


What should I do next?

---

### Post by Maestro23 on 2008-06-06
Run:

> sudo dpkg --configure -a

RootSudo: [https://help.ubuntu.com/community/RootSudo?highlight=(RootSudo](https://help.ubuntu.com/community/RootSudo?highlight=(RootSudo))

---

### Post by Duck2006 on 2008-06-06
Then run.

sudo apt-get update
sudo apt-get upgrade

---

### Post by furoido on 2008-06-06
Thanks Duck!

Sudo apt-get update worked fine, but when I tried to upgrade, got this:

andrew@andrew-desktop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run ‘apt-get -f install’ to correct these.
The following packages have unmet dependencies.
E: Unmet dependencies. Try using -f.

Is running upgrade necessary/important?

---

### Post by furoido on 2008-06-06
Just found something else after using update manager:

You have 1 broken package on your system! Use "broken" filter to locate it.

How do I locate/use 'broken' filter?!

---

### Post by iaculallad on 2008-06-06
On your terminal, try:

```
sudo apt-get install --fix-missing
```

---

### Post by Maestro23 on 2008-06-06
Also can open Synatpic: Edit>>Fix Broken Packages

---

