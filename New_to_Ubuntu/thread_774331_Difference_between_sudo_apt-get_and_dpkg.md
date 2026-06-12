---
title: "Difference between sudo apt-get and dpkg"
date: 2008-04-29
forum: New to Ubuntu
---

### Post by 7raTEYdCql on 2008-04-29
I am at present reading about the command line and trying to learn it.

I stumbled upon this doubt and wanted clarification.

What is the difference between 
```
$sudo apt-get
```
and 
```
$dpkg-deb
```

This is what i thought the difference is, please correct me if i am wrong.


Sudo apt-get is used to download packages which are stated in our download manager(Synaptic in the case of ubuntu).

dpkg is used to download packages from ...?(3rd part sites.  I'm not sure)

Can someone explain.

Does anyone have any reference websites from which i can actually study the command line from a newbie to a professional.

I have found sites but none of them are exhaustive.

Please help.

Thanking you.

---

### Post by Ek0nomik on 2008-04-29
[http://diablo.ucsc.edu/~wgscott/debian/apt-dpkg-ref.html](http://diablo.ucsc.edu/~wgscott/debian/apt-dpkg-ref.html)

Here is a tutorial you can follow:  [http://www.hypexr.org/bash_tutorial.php](http://www.hypexr.org/bash_tutorial.php)
More help:  [http://www.ss64.com/bash/](http://www.ss64.com/bash/)

---

### Post by DexterLB on 2008-04-29
sudo means "run as root"
apt-get downloads packages from archive AND third party sites.

dpkg can install a .deb package, stored on your hard disk. If it can download something, that's an add-on.
A GUI version of dpkg is gdebi

---

### Post by Eisenwinter on 2008-04-29
The difference is, dpkg is used to install DEBs you downloaded manually.

---

### Post by Monicker on 2008-04-29
Another link which might help:

[http://linuxhelp.blogspot.com/2005/12/concise-apt-get-dpkg-primer-for-new.html]("http://linuxhelp.blogspot.com/2005/12/concise-apt-get-dpkg-primer-for-new.html")

apt-get basically wraps around dpkg and simplifies the process of finding, installing, and maintaining packages.  dpkg does most of the grunt work behind the scenes.

---

### Post by forrestcupp on 2008-04-29
Synaptic is just a GUI frontend for apt that performs apt-get commands for you.

apt-get takes care of downloading programs from the repositories and installing the deb packages for you.  Apt-get uses dpkg to install the files.

The dpkg command is just the deb installer that installs debs that have already been downloaded.

There are many other uses for apt-get and dpkg, but that is the basics of how they work.

---

### Post by billgoldberg on 2008-04-29
> **DexterLB said:**
> sudo means "run as root"
apt-get downloads packages from archive AND third party sites.

dpkg can install a .deb package, stored on your hard disk. If it can download something, that's an add-on.
A GUI version of dpkg is gdebi

I'm pretty sure apt can only download from the repo's.

Or else apt:url would be a significant security risk.

---

### Post by forrestcupp on 2008-04-29
> **billgoldberg said:**
> I'm pretty sure apt can only download from the repo's.

Or else apt:url would be a significant security risk.

I think DexterLB was talking about 3rd party repos.  The OP was confused and thought that apt-get was only for supported repos and dpkg was for all 3rd party stuff.

---

### Post by stchman on 2008-04-29
> **i.mehrzad said:**
> I am at present reading about the command line and trying to learn it.

I stumbled upon this doubt and wanted clarification.

What is the difference between 
```
$sudo apt-get
```
and 
```
$dpkg-deb
```

This is what i thought the difference is, please correct me if i am wrong.


Sudo apt-get is used to download packages which are stated in our download manager(Synaptic in the case of ubuntu).

dpkg is used to download packages from ...?(3rd part sites.  I'm not sure)

Can someone explain.

Does anyone have any reference websites from which i can actually study the command line from a newbie to a professional.

I have found sites but none of them are exhaustive.

Please help.

Thanking you.

Instead of using dpkg use gdebi.  The gdebi command also installs needed dependencies.  Type gdebi --help for more info.

---

### Post by ubuntu-freak on 2008-04-29
The most simple way to look at it, is that dpkg won't download and install dependencies, but apt-get will. 
 
Gdebi is more than a GUI frontend for dpkg, as it will actually download and install every dependency when you double-click on a deb file from Getdeb.com etc.
 
Nathan

---

### Post by 7raTEYdCql on 2008-04-29
Thanks everyone for the response, i think i have understood the point.

Thanking you, once more.
Mehrzad

---

