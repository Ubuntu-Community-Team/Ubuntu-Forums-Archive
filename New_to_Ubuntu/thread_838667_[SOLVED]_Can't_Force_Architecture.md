---
title: "[SOLVED] Can't Force Architecture"
date: 2008-06-23
forum: New to Ubuntu
---

### Post by BGFG on 2008-06-23
Hi All,
Please take a look at my terminal output an tell me what could be wrong. 
The Skype file is sitting on my desktop.

reyn@reyn-desktop:~$ sudo dpkg -i --force-architecture skype-debian_2.0.0.72-1_i386.deb
dpkg: error processing skype-debian_2.0.0.72-1_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 skype-debian_2.0.0.72-1_i386.deb

thanks...

---

### Post by RomeReactor on 2008-06-23
Hi. You don't seem to be in the same directory as the Skype package; if you downloaded it to the desktop, try:
```
cd Desktop
```
and try installing it again.

---

### Post by Rocket2DMn on 2008-06-23
> **RomeReactor said:**
> Hi. You don't seem to be in the same directory as the Skype package; if you downloaded it to the desktop, try:
```
cd Desktop
```
and try installing it again.

+1
The terminal must be in the directory that the file is in.  Alternatively you can type the path as part of the command (while in your home folder):
```
sudo dpkg -i --force-architecture Desktop/skype-debian_2.0.0.72-1_i386.deb
```
Or from any folder, you can use the whole path:
```
sudo dpkg -i --force-architecture ~/Desktop/skype-debian_2.0.0.72-1_i386.deb
```
~ is short for your /home/username directory.

---

### Post by BGFG on 2008-06-23
Yup that was it, thanks a lot. :)

---

### Post by seicean on 2009-02-18
Thanks a LOT... solved my problem. But unfortuately, after forcing deb package, I get the errormessage:

> .deb has broken dependencies

I run *sudo apt-get install -f*, but still no result. 

At least I know how to force arhitecture from now on

---

### Post by RomeReactor on 2009-02-19
Seicean, if you're using Ubuntu 64 bit, you need to install ia32-libs in order to run 32 bit programs (in case you don't have them installed yet):
```
sudo aptitude install ia32-libs
```

Sorry for the late reply.

---

