---
title: "difference between bin and rpm"
date: 2012-12-17
forum: New to Ubuntu
---

### Post by sakthi8489 on 2012-12-17
Hi,

What is the difference between rpm and bin file installer? Is there any manager for bin like rpm manager? Can a bin installer created can be entered in such manager?

How to manage bin installers in ubuntu? Please let me know some package manager for bin files in ubuntu..

---

### Post by haqking on 2012-12-17
> **sakthi8489 said:**
> Hi,

What is the difference between rpm and bin file installer? Is there any manager for bin like rpm manager? Can a bin installer created can be entered in such manager?

How to manage bin installers in ubuntu? Please let me know some package manager for bin files in ubuntu..

.bin is an executable like Windows .exe.

you execute it

---

### Post by audiomick on 2012-12-17
You seem to be familiar with rpm packages. The equivalent for Ubuntu and all other Debian derivatives is .deb. These can be installed with a right click on the file and choose "install with software centre" or something to that effect.

You should always look in the software centre first, and see if what you want to install is in there.

---

### Post by sakthi8489 on 2012-12-17
Thank You Michael.

I have created some bin installer. I need it to display the installed packages in some sort of manager like rpm. I am using ubuntu server edition. Is it possible in ubuntu server edition to list all the software packages installed by me?

---

### Post by audiomick on 2012-12-17
I believe such a list is possible, at least those which have been installed via the package manager. I am not sure of the exact method from the terminal, though. You might find an indication in
```
man apt-get
```

I'm pretty sure the list is in one of the files mentioned towards the bottom of that.

---

### Post by haqking on 2012-12-17
> **sakthi8489 said:**
> Thank You Michael.

I have created some bin installer. I need it to display the installed packages in some sort of manager like rpm. I am using ubuntu server edition. Is it possible in ubuntu server edition to list all the software packages installed by me?

```
less /var/log/apt/history.log
```

---

### Post by Cavsfan on 2012-12-17
An RPM file is a Red Hat Package Manager file. I was under the impression RPM files are for distros other than Ubuntu.

---

### Post by Cavsfan on 2012-12-17
> **haqking said:**
> ```
less /var/log/apt/history.log
```

That is a pretty amazing command haqking.

---

### Post by haqking on 2012-12-17
> **Cavsfan said:**
> An RPM file is a Red Hat Package Manager file. I was under the impression RPM files are for distros other than Ubuntu.

They are though can still be used by converting with Alien.

However the OP asked what is the difference between a .bin and a .rpm

---

### Post by Cavsfan on 2012-12-17
> **Cavsfan said:**
> An RPM file is a Red Hat Package Manager file. I was under the impression RPM files are for distros other than Ubuntu.

> **haqking said:**
> They are though can still be used by converting with Alien.

However the OP asked what is the difference between a .bin and a .rpm

I guess you answered what a .bin file was and I answered what a .rpm file is.

---

### Post by sakthi8489 on 2012-12-17
thank you guys..

less /var/log/apt/history.log gives the list of packages installed using apt-get. But i just want to have my application there.. is there any way to do it?

---

### Post by audiomick on 2012-12-17
> **sakthi8489 said:**
> But i just want to have my application there.. is there any way to do it?

If you have installed something without using the package management system, I am not sure that there is any way of seeing it. That is the advantage of sticking to the package management system: the system then knows what is installed.

---

### Post by sakthi8489 on 2012-12-19
thanks.. How to install the application using the package management system?
or How to add the installer to the package management system?

---

### Post by sakthi8489 on 2012-12-19
How can i add my installation software in dpkg?

---

### Post by sakthi8489 on 2012-12-19
Is there any package manager for server based Ubuntu?
How to add my own application to that package manager and keep track of them?

---

### Post by audiomick on 2012-12-19
Ubuntu server uses APT for package managent, same as standard Ubuntu and all Debian derivatives.
[http://en.wikipedia.org/wiki/Advanced_Packaging_Tool]("http://en.wikipedia.org/wiki/Advanced_Packaging_Tool")


If I have understood you correctly you have a program you have written, and wish to intergrate it into the package management system. To do that, you will need to create a .deb package. I haven't done this, but a bit of searching found this, which looks like it should help.
[http://www.ibm.com/developerworks/linux/library/l-debpkg/index.html]("http://www.ibm.com/developerworks/linux/library/l-debpkg/index.html")

---

