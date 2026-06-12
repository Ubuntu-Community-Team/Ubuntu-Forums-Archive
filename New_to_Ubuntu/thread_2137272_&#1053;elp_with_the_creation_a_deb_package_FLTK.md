---
title: "&#1053;elp with the creation a deb package FLTK"
date: 2013-04-20
forum: New to Ubuntu
---

### Post by dias75 on 2013-04-20
I'm using Ubuntu 10.10 

compile FLTK Version 1.3.2

$ ./configure
$ make
$ sudo checkinstall -D
...
=== installing FL ===
Installing include files in /usr/local/include...
/usr/bin/install: can not be changed the access rights «/usr/local/include/FL»: No such file or directory
make[1]: *** [install] Error 1
make: *** [install] Error 1

****  

Installation failed. Creation of a package is canceled. Cleared...OK--------
In what here reason? Advice please!

---

### Post by 3rdalbum on 2013-04-20
> **dias75 said:**
> I'm using Ubuntu 10.10

Problem 1: Ubuntu 10.10 is well and truly out of support. You must upgrade to 12.04, 12.10 or 13.04 (out soon). Your system is vulnerable as it no longer gets security updates, and you can't access the software repositories either.

> /usr/bin/install: can not be changed the access rights «/usr/local/include/FL»: No such file or directory

Problem 2: Try creating the directory /usr/local/include/FL.

---

### Post by dias75 on 2013-04-20
> **3rdalbum said:**
> Problem 2: Try creating the directory /usr/local/include/FL.

Yes, it helped. Thank you! 
It took a few more directories. The terminal is was showing. And then I installed Dillo browser (the latest version at the moment). To him is also it took several directories.
> Problem 1: Ubuntu 10.10 is well and truly out of support. You must  upgrade to 12.04, 12.10 or 13.04 (out soon). Your system is vulnerable  as it no longer gets security updates, and you can't access the software  repositories either.
Repositories were transferred to the server of the old releases. And once again available. 
Simply, they are not updated. But there are installing from source. 
I'm used to 10.10 and do not want to change it. :)
---------
My English is very bad - I write through the translator.

---

