---
title: "how to install some debian package on ubuntu"
date: 2012-09-12
forum: New to Ubuntu
---

### Post by syednasirraza on 2012-09-12
sometimes,,, if i m looking for som software over net,,, i dont get specifically for ubuntu,,,i get it for linux or in the name as debian package...how to install it on ubuntu if it is for redhat or debian ???

---

### Post by deadflowr on 2012-09-12
Preferably, if you intend to install packages from sources outside the Ubuntu repos, or the software center, go with deb. 
Ubuntu is a debian based distro, so .deb install with little effort, simply double-click, or right-click and select software center, and follow standard installation procedure.
Don't download RPMs, as they are not native-built for debian-based distributions. There is a program called alien which can convert rpms to debs, but it can be complex, and sometimes the package doesn't quite convert properly.

---

### Post by GreatDanton on 2012-09-12
If the package is for debian with the ending  .deb, then you can double click on it will open software center. After that just click the install button.

---

### Post by snowpine on 2012-09-12
You've heard the expression "Linux is Open Source"? This means you can download the application's source code (usually in tar.gz or similar format) and compile it for Ubuntu. Here are a couple of easy how-to guides:

[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)
[https://help.ubuntu.com/community/CompilingSoftware](https://help.ubuntu.com/community/CompilingSoftware)

---

### Post by CharlesA on 2012-09-12
What software are you trying to install?

---

### Post by vasa1 on 2012-09-12
> **snowpine said:**
> You've heard the expression "Linux is Open Source"? This means you can download the application's source code (usually in tar.gz or similar format) and compile it for Ubuntu. Here are a couple of easy how-to guides:

[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)
[https://help.ubuntu.com/community/CompilingSoftware](https://help.ubuntu.com/community/CompilingSoftware)

> Easy meaning "easier than tearing your hair out and then screaming about how much Linux sucks while running around the room". Not actually easy
From the first link ;)

---

### Post by snowpine on 2012-09-12
> **vasa1 said:**
> From the first link ;)

Not sure I get it. 

Easiest is to install applications with a couple of mouse clicks in the Software Center, from a library of 30,000+ tested and trusted applications.

If you must go outside those easy-to-install apps, then isn't it more hassle-free to install the documented upstream source code than to attempt conversion of an .rpm for Fedora or a .deb for a Debian release that may-or-may-not be compatible with your Ubuntu release? Compiling from source is a basic Linux 101 skill that is easy and well documented. 

Ultimately, however, **CharlesA** has the best advice in the entire thread: "What software are you trying to install?" trumps any hypothetical discussion or FUD.

---

### Post by josephmills on 2012-09-12
```
sudo dpkg -i name_of_debian_package.deb
```
too remove 
```
sudo dpkg -P name_of_package.deb
```
so save your debs. 

Most if not all software that is in deb forms are in the Ubuntu repo's and or a repo's that is close by. I hope that this helps and maybe just use software center. :)

---

### Post by newb85 on 2012-09-12
> **snowpine said:**
> Ultimately, however, **CharlesA** has the best advice in the entire thread: "What software are you trying to install?" trumps any hypothetical discussion or FUD.

Agreed.  Giving a target answer requires more detailed info on the question.

That said, I will throw my hat into the hypothetical discussion.  It's often better to find a PPA with the desired package than to directly download the *.deb.  Automatic updates (e.g., bug fixes, etc.)  Of course they must be a trusted PPA, but then, the same applies to the *.deb.

---

