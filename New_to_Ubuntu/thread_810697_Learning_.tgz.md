---
title: "Learning .tgz"
date: 2008-05-28
forum: New to Ubuntu
---

### Post by nilsolaris on 2008-05-28
Where would i need to place vmware-any-any-update117.tgz to run it through the terminal?

---

### Post by Monicker on 2008-05-28
That is an archive, and you will need to extract it.  You can right click on it from Nautilus and select Extract Archive.

Or from the console:

```
tar xzvf vmware-any-any-update117.tgz
```


The extracted contents should have a README or INSTALL file explaining what you need to do from there.

---

### Post by zvacet on 2008-05-28
Is [this]("http://www.howtoforge.com/vmware-server-on-ubuntu8.04") of any help to you?

---

### Post by leon.hh on 2008-05-28
Hold on... installing vmware from the source code it's a little tricky, you will need to download the sources of your running kernel (which it's not big deal, but slightly bothering). However, the file you got it's an update not an installer.

If you are running Debian or Ubuntu you can install vmware-server from the backports repositories with apt-get install vmware-server.

However, vmware it's NOT open source, I strongly recommend VirtualBox-ose (ose means Open Source Edition) which is in the official repositories of both  Debian and Ubuntu and it's easy to install and use

Let me know if you are interested in the Virtual Machines issue to give you more information about it, if you just wanted to open the .tar file and have no interest in VM, simply follow the instructions of Monicker

---

