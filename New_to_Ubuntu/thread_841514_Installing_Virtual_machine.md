---
title: "Installing Virtual machine"
date: 2008-06-26
forum: New to Ubuntu
---

### Post by betterthanjordan79 on 2008-06-26
im tryin to install a virtual machine on linux so i can use xp/vista on it but i keep gettin this error wen i go to install it 

> VirtualBox will not start until this problem is fixed. Please consult /var/log/vbox-install.log to find out why the kernel module does not compile. Most probably the kernel sources were not found. Install them and execute

  /etc/init.d/vboxdrv setup

as root.

cold someone please help me over come this problem.

im using this walk through - [http://n00buntu.blogspot.com/](http://n00buntu.blogspot.com/) - its about half way down the page on it  thanks in advance for all help given

---

### Post by NetworkGuy on 2008-06-26
You haven't installed the kernel module.  Using synaptic, search on virtualbox and install the virtualbox-ose-module-generic (or something like that).   It will install the kernel module you need.

Also, did you make yourself a member of the vboxdrv group?

---

### Post by betterthanjordan79 on 2008-06-26
yh i did make it the user groups etc...still is given me the same error...

---

### Post by WRDN on 2008-06-26
Try running the following command in the Terminal:

```
sudo /etc/init.d/vboxdrv setup
```

This will recompile the kernel module, if available.

---

