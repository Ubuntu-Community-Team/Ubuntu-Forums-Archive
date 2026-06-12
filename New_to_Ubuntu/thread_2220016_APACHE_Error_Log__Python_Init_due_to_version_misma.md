---
title: "APACHE Error Log : Python Init due to version mismatch"
date: 2014-04-26
forum: New to Ubuntu
---

### Post by deAndro on 2014-04-26
Hi, 

I am new to LINUX (Ubuntu) and running 2 VM's (12.4) for testing and one  professional host on a german host provider (strato / ubuntu 12.4).
On my VM's I have installed mercurial with hgweb which is running well. But on my professional host I cannot get it running and I suggest the following lines from /var/log/apache2/error.log explain the reason: 

```
[Sat Apr 26 14:54:55 2014] [error] python_init: Python version mismatch, expected '2.7.2+', found '2.7.3'.
[Sat Apr 26 14:54:55 2014] [error] python_init: Python executable found '/usr/bin/python'.
[Sat Apr 26 14:54:55 2014] [error] python_init: Python path being used '/usr/lib/python2.7/:/usr/lib/python2.7/plat-linux2:/usr/lib/python2.7/lib-tk:/usr/lib/python2.7/lib-old:/usr/lib/python2.7/lib-dynload'.
[Sat Apr 26 14:54:55 2014] [notice] mod_python: Creating 8 session mutexes based on 150 max processes and 0 max threads.
[Sat Apr 26 14:54:55 2014] [notice] mod_python: using mutex_directory /tmp
```

Am I right? How and where do I have to solve that. I already tried to remove python and install it again with same effect. 

Regards
deAndro

---

### Post by deAndro on 2014-04-27
solved.... with....:
$ apt-get remove libapache2-mod-python libapache2-mod-wsgi 
$ apt-get build-dep libapache2-mod-python libapache2-mod-wsgi

---

