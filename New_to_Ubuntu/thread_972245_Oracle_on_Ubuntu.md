---
title: "Oracle on Ubuntu?"
date: 2008-11-05
forum: New to Ubuntu
---

### Post by griffo69 on 2008-11-05
Can Oracle be installed on ubuntu?
If so how?
New to ubuntu

---

### Post by Zzl1xndd on 2008-11-05
Never tried it but I did find this

[http://www.oracle.com/technology/tech/linux/install/xe-on-kubuntu.html](http://www.oracle.com/technology/tech/linux/install/xe-on-kubuntu.html)

---

### Post by janpla on 2008-11-27
This is actually quite easy. First go and get the Enterprise Edition from oracle:

[http://www.oracle.com/technology/index.html](http://www.oracle.com/technology/index.html)

Or possibly one of the others, but I can't really see the point, personally.

Create a database admin group, dba, and the user oracle in that group. Log in as oracle (or su - oracle) and unpack the downloaded oracle file. Read the installation doc and check that you have all the relevant libraries and kernel parameters etc - this is important.

Find the installer: runInstaller. Run it as user oracle. It will complain at some point because you don't have rpm installed, but you can click on the items to comfirm that it is OK anyway. Continue until installation starts; it doesn't use rpm to unpack Oracle stuff, only to check that necessary libraries are installed.

If there are any errors during installation, read the message carefully - there will usually be a reference to a log file, which you should then read. There is also a user support forum on the page listed above.

---

