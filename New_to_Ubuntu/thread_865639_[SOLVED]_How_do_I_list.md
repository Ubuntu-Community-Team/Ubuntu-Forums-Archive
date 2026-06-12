---
title: "[SOLVED] How do I list?"
date: 2008-07-20
forum: New to Ubuntu
---

### Post by neurostu on 2008-07-20
How do I get a list the packages I have installed recently with apt-get?

---

### Post by scragar on 2008-07-20
```
apt-cache pkgnames | less
```will list all packages on the system,

you can list deb packages downloaded recently, sorting by date or whatever as required:
```
ls **-t** /var/cache/apt/archives/*
```remove the -t to stop sorting by time and just list all packages.

---

### Post by neurostu on 2008-07-20
Thanks... but i need to know how to sort the packages by the date they were installed, and possibly examine the installation dates...

---

### Post by Dr Small on 2008-07-20
How are the currently sorted ... alphabetically?
This may help, though:
```
man sort
```

---

### Post by scragar on 2008-07-20
use:```
ls -l -t /var/cache/apt/archives/*
```
if you need a lot of details, you only really need package name and date though.

---

### Post by neurostu on 2008-07-20
Scragar, I appreciate both suggestions but neither one lists the recently installed packages...

For example I know I installed a few packages today but none of them are listed in either of the two options...

Dr. Small, I have experience using sort, thanks though

---

### Post by ibuclaw on 2008-07-20
To further scragar's command, this will show the 10 newest deb files that you downloaded,so they should be the last items you installed.
```
ls -l -t /var/cache/apt/archives/* | head -n11 | tail -n10 | sed 's/^.*\///g;s/_.*$//g'
```

Although, you could always just check your bash_history file.
```
cat ~/.bash_history | grep "apt-get install" | sed 's/^.*-get install //g' | tail -n 10 | tac
```

Regards
Iain

---

### Post by scragar on 2008-07-20
bash_history only shows things installed from the terminal, so it's not as good a solution as listing files in the cache. The problem is that the cache can be cleared, and it looks like it has in this case. As I said anyway, this is packages downloaded, not installed.

Shame apt doesn't keep logs itself other than programs installed in what appears to be a fairly random order.

---

### Post by NullHead on 2008-07-20
Will this help?:```
sudo cat /var/log/apt/term.log
```

---

### Post by zvacet on 2008-07-21
**synaptic>file tab>history**

---

### Post by neurostu on 2008-07-21
> **NullHead said:**
> Will this help?:```
sudo cat /var/log/apt/term.log
```

Thanks!

---

