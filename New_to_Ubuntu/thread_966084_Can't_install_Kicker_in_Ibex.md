---
title: "Can't install Kicker in Ibex"
date: 2008-11-01
forum: New to Ubuntu
---

### Post by mishathegoat on 2008-11-01
Hey everyone! I installed a fresh copy of Ubuntu Desktop 8.10 (x86) and I can't seem to install kicker. I have already installed all the updates.. When I try to install I get this message:

```
misha@misha-laptop:~$ sudo apt-get install kicker
[sudo] password for misha: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package kicker is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  kdelibs-data
E: Package kicker has no installation candidate

```

---

### Post by mishathegoat on 2008-11-02
-Bump- Still no luck finding a solution..

---

### Post by hellion0 on 2008-11-02
If you're using 32-bit Ubuntu, you can find a .deb for Kicker here:
```
https://launchpad.net/ubuntu/intrepid/i386/kicker/4:3.5.9-0ubuntu7
```

However, do note what it replaces before you install it. Also, I'm not a KDE expert, so I don't know if it will work with KDE4 properly.

---

### Post by mishathegoat on 2008-11-02
Dang, didn't work.. I get a message that says

```

Error: Dependency is not satisfiable: kdebase-data

```

I installed kdebase, kdebase-bin, kdebase-data, kdebase-dev, kdebase-runtime, kdebase-runtime-bin-kde4, kdebase-runtime-data and I get the same message

---

### Post by mishathegoat on 2008-11-03
-Bump-

---

### Post by mishathegoat on 2008-11-04
-Bump-

Still can't seem to get it installed..

---

### Post by LowSky on 2008-11-04
Do you trying to install KDE or just kicker?

sudo apt-get install kubuntu-desktop

might be a last ditch to install

---

### Post by mishathegoat on 2008-11-04
Yeah I only want to install kicker. I thought about installing kubuntu as a last resort.. I'd rather not though

[EDIT] I installed kubuntu-desktop and tried to start kicker. I got this message:
```
bash: kicker: command not found
```

---

### Post by LowSky on 2008-11-04
I don't think you can use Kicker with Gnome... I could be wrong?

---

### Post by mishathegoat on 2008-11-04
According to [this](http://ubuntuforums.org/archive/index.php/t-584588.html) post, you can. And it was as easy as:

```
sudo apt-get install kicker
```

---

### Post by LowSky on 2008-11-04
8.10 also uses a different version of KDE than 7.04/7.10 had installed (KDE 3.5 vs KDE 4.1)

Could be part of your issue

---

### Post by mishathegoat on 2008-11-04
Hmmm I'm able to install and run kicker after a fresh install of 8.04.. But I'm sure you're right in that 8.10 probably uses a very different version of KDE

So does anyone have any idea how to initialize kicker in the newer versions of KDE?

---

