---
title: "E: Unable to locate package usbmount"
date: 2012-09-17
forum: New to Ubuntu
---

### Post by samansad on 2012-09-17
Dear all
I am new in Ubuntu and I wanted to mount my usb drive but when I wanted to install the usbmount I received this error:

```
E: Unable to locate package usbmount
```

I did ```
cat /etc/apt/sources.list
``` and bellow is the result:

```
deb cdrom:[Ubuntu-Server 12.04.1 LTS _Precise Pagolin_ - Release i386 (20120817.3)]/ precise main restricted
```

I am using Ubuntu Server and as you know there is no GUI.

Thank you for your help

---

### Post by jerrrys on 2012-09-17
Is that it?  Is that your whole sources list?

---

### Post by samansad on 2012-09-20
> **jerrrys said:**
> Is that it?  Is that your whole sources list?

yup it was only that. But I realized it is that much small because none of the packages from Ubuntu were installed. So I re-installed Ubuntu and it solved the problem.
I just learned that during installation of Ubuntu I must not install any package and I should install one by one after installation. I don't know why I cannot install them during installing the Ubuntu.

Anyway Thank you for your reply.

---

