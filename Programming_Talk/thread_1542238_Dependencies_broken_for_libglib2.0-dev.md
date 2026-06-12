---
title: "Dependencies broken for libglib2.0-dev"
date: 2010-07-30
forum: Programming Talk
---

### Post by BillRebey on 2010-07-30
I'm using Ubuntu 9.10, and I'm trying to install the dbus libraries.

Specifically, the glib interface library messes up. When I run:

```
sudo apt-get install libdbus-glib-1-dev
```

I get:

```
The following packages have unmet dependencies:
  libdbus-glib-1-dev: Depends: libglib2.0-dev 
        but it is not going to be installed
```

So naturally I attempt to install libglib2.0-dev, as suggested by the error above:

```
sudo apt-get install libglib2.0-dev
```

and I get

```
The following packages have unmet dependencies:
  libglib2.0-dev: Depends: libglib2.0-0 (= 2.22.2-0ubuntu1) 
        but 2.22.3-0ubuntu1 is to be installed

```
Now what?? 

What is 2.22.2-0ubuntu1?  It's not a package; it appears  to be some kind of version of libglib2.0-0.  If  that's the case,  how to I specify that 2.22.2-0ubuntu1 should be installed instead of 2.22.3-0ubuntu1 so  that the indicated dependency is satisfied?  This seems like it should be a real simple thing, and my work is at a standstill because of this.  

Anybody know how to fix this?  I really appreciate  any help I can get.

---

### Post by Bachstelze on 2010-07-30
What's your sources.list?

---

### Post by BillRebey on 2010-07-30
Sources list is one entry:

```
deb http://ubuntu.src.cn/ubuntu-ports/ karmic main  universe restricted multiverse

```

The platform is a SmartQ-V7 ARM11-based tablet PC.  The sources.list referenced above is what it came with.

---

### Post by Bachstelze on 2010-07-30
Use this instead.  Right now, you're not getting any of the updates.

```
deb http://ports.ubuntu.com/ubuntu-ports/ karmic main restricted universe multiverse
deb http://ports.ubuntu.com/ubuntu-ports/ karmic-updates main restricted universe multiverse
deb http://ports.ubuntu.com/ubuntu-ports/ karmic-security main restricted universe multiverse
```

---

### Post by notunnemo on 2011-12-01
I was trying to install xawtv.
But when I do
sudo apt-get install xawtv

I get the error message 

libglib2.0-0: Breaks: gvfs (< 1.8) but 1.4.1-0ubuntu1 is to be installed
  ppp: Breaks: network-manager (<= 0.8.0.999-1) but 0.8~a~git.20091013t193206.679d548-0ubuntu1 is to be installed

What do you think is the source of the problem?

---

