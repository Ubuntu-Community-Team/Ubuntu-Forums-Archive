---
title: "installing build-essentials"
date: 2008-10-25
forum: Packaging and Compiling Programs
---

### Post by kcode on 2008-10-25
my desktop can not access internet (as it is not recognising the modem) and it also has some problem with CD_ROM. i cannot do programming in it as i dont have build essentials installed. 
how can i install it manualy?
i found a .deb package of build-essenttal in ubuntu installation CD. But im unable to install using it.(using ubuntu 8.04)

thanks

---

### Post by pdwerryhouse on 2008-10-25
build-essential is a virtual package; it exists only to depend on other packages, and hence will pull those in when it is installed using apt-get.

So, if you are trying to install it with dpkg -i, it will fail. Instead, use apt-get to install it from your cdrom. You will need to make sure that your /etc/apt/sources.list file contains references to your cdrom in it.

If it doesn't, use apt-cdrom to add it. So, the entire process might look something like this:

```
apt-cdrom add
apt-get update
apt-get install build-essential
```

---

### Post by kcode on 2008-11-09
> **pdwerryhouse said:**
> build-essential is a virtual package; it exists only to depend on other packages, and hence will pull those in when it is installed using apt-get.

So, if you are trying to install it with dpkg -i, it will fail. Instead, use apt-get to install it from your cdrom. You will need to make sure that your /etc/apt/sources.list file contains references to your cdrom in it.

If it doesn't, use apt-cdrom to add it. So, the entire process might look something like this:

```
apt-cdrom add
apt-get update
apt-get install build-essential
```

Well, the problem is that, my CD-ROM is not working properly, i think their is some hardware issues. So what i am thinking of doing is, copying the package from CD-ROM (using a different machine) into a pen-drive, and then installing the package using PD. Is this possible??

thanks

---

### Post by pdwerryhouse on 2008-11-10
Installing just the build-essential package won't be enough; it doesn't contain any data itself, you'll also need to copy all of the packages that it depends upon.

---

### Post by kcode on 2008-11-10
> **pdwerryhouse said:**
> Installing just the build-essential package won't be enough; it doesn't contain any data itself, you'll also need to copy all of the packages that it depends upon.

And how do i get to know, on which package it depend?

---

### Post by Sorivenul on 2008-11-10
build-essentials dependencies:
[For Hardy]("http://packages.ubuntu.com/hardy/build-essential")
[For Intrepid]("http://packages.ubuntu.com/intrepid/build-essential")

Remember also that many, if not all, of those dependencies have dependencies of their own.

---

### Post by kcode on 2008-11-11
> **Sorivenul said:**
> 
Remember also that many, if not all, of those dependencies have dependencies of their own.

Bump!!

---

