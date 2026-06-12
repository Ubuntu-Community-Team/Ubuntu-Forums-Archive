---
title: "getting error message while updating"
date: 2013-05-27
forum: New to Ubuntu
---

### Post by rahul_bhise on 2013-05-27
yesterday there was a update avalable in update mannager. but when i clicker on update, they showed an error message,

Requires installation of untrusted packages
The action would require the installation of packages from not authenticated sources.

gvfs gvfs-backends gvfs-bin gvfs-common gvfs-daemons gvfs-fuse gvfs-libs linux-generic-pae linux-headers-3.2.0-44 linux-headers-3.2.0-44-generic-pae linux-headers-generic-pae linux-image-3.2.0-44-generic-pae linux-image-generic-pae linux-libc-dev

i dont wante to install from a untrusted package but i see a resent linux kernal is also in there.

---

### Post by fantab on 2013-05-27
Open 'Software Center' -> Edit -> 'software sources' -> Ubuntu Software and enable _source code_, if it is not.

Then close the Software Center... 

Open Termianal and run:
sudo apt-get update 
If you get any errors then post the output here, if not:
sudo apt-get upgrade

---

### Post by ibjsb4 on 2013-05-27
These are not untrusted sources, looks like your missing a key.  The first fix (thanks cortman) should work for you.

[http://cortman.wordpress.com/2012/02/27/how-to-fix-gpg-errors-in-ubuntu/](http://cortman.wordpress.com/2012/02/27/how-to-fix-gpg-errors-in-ubuntu/)

---

### Post by mustafi05 on 2013-06-01
ucan even import your missing keys through yppa manager

---

### Post by rahul_bhise on 2013-06-03
> **fantab said:**
> Open 'Software Center' -> Edit -> 'software sources' -> Ubuntu Software and enable _source code_, if it is not.

Then close the Software Center... 

Open Termianal and run:
sudo apt-get update 


this solved my problem. THANKS
sorry for the late responce

---

