---
title: "Quick question: which package has the documentation for posix/kernel API ?"
date: 2007-02-12
forum: Programming Talk
---

### Post by mercurysquad on 2007-02-12
Hi guys,

Just started with Computer architecture / Operating Systems class at univ. Our programming environment for the lab is Solaris on the lab clusters and Linux otherwise. I was wondering, which package contains the documentation for the POSIX or Linux kernel system calls? For example, if I type **man 2 pthreads** or **man execve** on the Solaris nodes, the appropriate man page shows up. However, on my Ubuntu laptop I get a message saying no manual entry was found. About 20-30% of the keywords work, since I have the build-essential package installed, but most do not. E.g. **man pthreads** works but **man pthread_create** does not.

I also installed linux-doc or something similar. Didn't help. Then I rummaged through all -doc packages but it got really tedious sorting through them trying to find the package that has the docs I am looking for.

Any hints?

EDIT: Found it!   **manpages-posix**, **manpages-posix-dev** and a ton of other manpages-*  :D

---

### Post by jblebrun on 2007-02-12
Why delete it? It might help someone else searching for a similar answer later!

---

### Post by Zanicar on 2007-03-21
I am looking for the pthread_create man pages too... But the posix manpages is no longer listed under packages. I tried searching for the packages listed in the fisrt post, namely manpages-posix and manpages-posix-dev, but didn't find it.

I did install the manpages and manpages-dev packages but they have nothing on pthreads_create. I heard a friend mention something about repositories that have to point to the "right stuff" in order to get access to certain packages...

Help will be much appreciated!

Thanks

---

### Post by WW on 2007-03-21
The packages **manpages-posix** and **manpages-posix-dev** are in the **multiverse** repository, as you can see with the result of this search at packages.ubuntu.com: [http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=manpages-posix&searchon=names&subword=1&version=all&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=manpages-posix&searchon=names&subword=1&version=all&release=all)

To enable to multiverse repository, look here: [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

---

### Post by Zanicar on 2007-03-21
Good stuff, Thanks!

...everything is working now and I got all the packages I needed... :D

---

