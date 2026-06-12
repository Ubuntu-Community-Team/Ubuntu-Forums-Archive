---
title: "create rpm package"
date: 2009-04-15
forum: Programming Talk
---

### Post by hamid206 on 2009-04-15
How I can create rpm package in debian base distro .
I read this [tutorial]("http://www.ibm.com/developerworks/library/l-rpm1/") for create rpm package , and I see some where like /usr/src/redhat/SOURCES that ,isnt in debian base distor .if I don't want use alien for convert deb to rpm ,and I want create rpm package manual. what should i do ?

---

### Post by cabalas on 2009-04-15
Alien ([http://kitenet.net/~joey/code/alien/](http://kitenet.net/~joey/code/alien/)) - which is available in the repos - can convert packages from one format to another, if you have already made  a .deb you can just convert it.   However from what I have been led to believe this does have it's issues and can create packages which might severely screw up a system.

Personally I would just install fedora in a VM and create the package in there, that way at lease you can test your rpm as well.

---

