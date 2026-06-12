---
title: "Dependencies problem"
date: 2012-06-11
forum: New to Ubuntu
---

### Post by foreveraashu on 2012-06-11
Can someone help me find a solution to the following errors. I am using Ubuntu 9.04.

Depends: libboost-filesystem1.34.1 (>= 1.34.1-8) but it is not installable
          Depends: libboost-serialization1.34.1 (>= 1.34.1-8) but it
is not installable
          Depends: libboost-test1.34.1 (>= 1.34.1-8) but it is not installable
          Depends: libxerces-c28 but it is not installable
          Depends: python2.5 (>= 2.5) but it is not installable
          Depends: python-twisted but it is not installable
          Depends: python-simplejson but it is not installable
          Depends: python-mako but it is not installable
          Depends: python-openssl but it is not installable
 noxext: Depends: tmpreaper but it is not installable

---

### Post by coffeecat on 2012-06-11
> **foreveraashu said:**
> Can someone help me find a solution to the following errors. I am using Ubuntu 9.04.

Ubuntu 9.04 is no longer supported. It went end-of-life in October 2010 and the repositories are closed. That is why you are getting "not installable" errors. You need to make a fresh install of a supported version of Ubuntu. An upgrade from 9.04 would be difficult or impossible because 9.10 is also unsupported now.

Which app are you trying to install?

---

### Post by deadflowr on 2012-06-11
The repos for 9.04 are gone.
+1 to what coffeecat said.

---

### Post by foreveraashu on 2012-06-11
I wanted to install SNAC openflow controller on the older ubuntu machine to check the functionality of the controller.I am linux newbie. Any options to make it work?

---

### Post by Michael Dooley on 2012-06-11
There are repositories for old releases. You might try looking at the page below:

[http://old-releases.ubuntu.com/releases/jaunty/](http://old-releases.ubuntu.com/releases/jaunty/)

Good luck foreveraashu.

Also, you might try looking here:

[http://superuser.com/questions/339537/where-can-i-get-theold-repositories-for-ubuntu-9-04-jaunty](http://superuser.com/questions/339537/where-can-i-get-theold-repositories-for-ubuntu-9-04-jaunty)

---

### Post by foreveraashu on 2012-06-12
Hey Michael  thank you so much for your reply.. I tried updating the /etc/apt/sources.list with the links but it didn't help solve the issue.

---

### Post by Michael Dooley on 2012-06-13
You probably already know about the SNAC wiki.

[https://github.com/bigswitch/snac/wiki](https://github.com/bigswitch/snac/wiki)

I would correspond with those people about your dependency problems. It appears as if you need to have a specialized snac repository in your sources list.

Good luck foreveraashu.

---

