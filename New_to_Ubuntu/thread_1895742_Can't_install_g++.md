---
title: "Can't install g++"
date: 2011-12-15
forum: New to Ubuntu
---

### Post by erelsgl on 2011-12-15
I try to install build-essential and get the following output:

```
erelsgl@ubuntu:/etc/apt$ sudo apt-get install build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.
2 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up g++ (4:4.4.3-1ubuntu1) ...
update-alternatives: error: alternative path /usr/bin/g++ doesn't exist.
dpkg: error processing g++ (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of build-essential:
 build-essential depends on g++ (>= 4:4.3.1); however:
  Package g++ is not configured yet.
dpkg: error processing build-essential (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          Errors were encountered while processing:
 g++
 build-essential
E: Sub-process /usr/bin/dpkg returned an error code (1)

```


And g++ does not work:

```
erelsgl@ubuntu:/etc/apt$ which g++
erelsgl@ubuntu:/etc/apt$ 

```

---

### Post by oldos2er on 2011-12-15
Post moved to its own thread.

---

### Post by TeoBigusGeekus on 2011-12-15
Could [this]("http://superuser.com/questions/368233/cannot-install-g-on-ubuntu") be of any help?

---

