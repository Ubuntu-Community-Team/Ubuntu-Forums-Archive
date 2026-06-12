---
title: "Recreate my /etc/apt/sources.list file?"
date: 2008-07-19
forum: New to Ubuntu
---

### Post by mista_eng on 2008-07-19
Hey guys, I am trying to recreate my /etc/apt/sources.list file since I accidentally deleted it. All I need is a reference and I will copy and paste or type it up. 

I was trying to figure out why my sudo apt-get update or apt-get install wget wasn't working on my fresh install of Ubuntu 8.04.1 JeOS. All in the name of trying to get dynamips/dynagen running on JeOS. 

Any help is appreciated, thanks!

---

### Post by braddcadd on 2008-07-19
[http://tuxicity.wordpress.com/sourceslist-for-ubuntu-hardy-heron-810/](http://tuxicity.wordpress.com/sourceslist-for-ubuntu-hardy-heron-810/)

---

### Post by neurostu on 2008-07-19
```

deb http://us.archive.ubuntu.com/ubuntu/ hardy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy main restricted

deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-updates main restricted
deb http://us.archive.ubuntu.com/ubuntu/ hardy universe
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy universe
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-updates universe

deb http://us.archive.ubuntu.com/ubuntu/ hardy multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy multiverse
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-updates multiverse

deb http://security.ubuntu.com/ubuntu hardy-security main restricted
deb-src http://security.ubuntu.com/ubuntu hardy-security main restricted
deb http://security.ubuntu.com/ubuntu hardy-security universe
deb-src http://security.ubuntu.com/ubuntu hardy-security universe
deb http://security.ubuntu.com/ubuntu hardy-security multiverse
deb-src http://security.ubuntu.com/ubuntu hardy-security multiverse

```

---

