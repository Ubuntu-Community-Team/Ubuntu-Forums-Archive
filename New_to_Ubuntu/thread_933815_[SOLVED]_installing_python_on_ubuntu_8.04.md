---
title: "[SOLVED] installing python on ubuntu 8.04"
date: 2008-09-29
forum: New to Ubuntu
---

### Post by shadow120 on 2008-09-29
ok im new to ubuntu and i cant figer this out im trying to install python 2.5.2 i downloaded the .tgz file and extracted it to my desktop and now im lost the readme says 

To start building right away (on UNIX): type "./configure" in the
current directory and when it finishes, type "make".  This creates an
executable "./python"; to install in /usr/local, first do "su root"
and then "make install".

and i cant make it work any advice would help thanks

---

### Post by lovinglinux on 2008-09-29
As far as know, python is installed by default. Nevertheless, you can install it from Synaptic. The package is there. No need to download the tgz file and compile it.

---

### Post by OutOfReach on 2008-09-29
Python is already installed in Ubuntu.
If you accidently removed it, it can be installed again just search 'python' in Synaptic.

---

### Post by lovinglinux on 2008-09-29
You can also run this command on a terminal

```
sudo apt-get install python
```

If it is already installed you will receive a message saying that python is already the newest version.

---

### Post by shadow120 on 2008-09-29
ok i feel stupid now thanks for the help

---

### Post by lovinglinux on 2008-09-29
Please don't forget to mark the thread as solved using the thread tools menu.

---

