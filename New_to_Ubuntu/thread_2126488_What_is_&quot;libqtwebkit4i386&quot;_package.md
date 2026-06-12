---
title: "What is &quot;libqtwebkit4:i386&quot; package"
date: 2013-03-17
forum: New to Ubuntu
---

### Post by bipinvish on 2013-03-17
I am trying to install GNOME in my Ubuntu 12.10 and end up with :

```
root@bipin-VPCYB25AG:/home/bipin# sudo apt-get install gnome-shell
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package libqtwebkit4:i386 needs to be reinstalled, but I can't find an archive for it.
root@bipin-VPCYB25AG:/home/bipin# 

```
What is that happening and now what I have to do to solve this problem.

Thanx in advance.


Bipin Vishwakarma
(b.vish@live.com)

---

### Post by sanderj on 2013-03-17
I would run:

```
sudo apt-get update && sudo apt-get upgrade
```

and see what happens then.

---

### Post by bipinvish on 2013-03-18
Hey Buddy thanx for reply 
Actually I am using amd64 is that any problem.
I think i386 & amd64 versions of webkit failed to load on my system.

---

