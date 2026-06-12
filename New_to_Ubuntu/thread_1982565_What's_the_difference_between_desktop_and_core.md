---
title: "What's the difference between desktop and core?"
date: 2012-05-18
forum: New to Ubuntu
---

### Post by cshin9 on 2012-05-18
If I want to do a minimal install, then install a desktop, there are apparently three [ways]("https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall#A10.10.2B-_.2832_and_64_Bit.29").

[LIST=1]
[*]```
apt-get install lubuntu-desktop
```
[*]```
apt-get install --no-install-recommends lubuntu-desktop
```
[*]```
apt-get install lubuntu-core
```
[/LIST]
I know the difference between the first and the second is that the second won't install any recommended packages, but why is there a "core" then? Is it supposed to be even more bare-bones? What is the difference in functionality between the second and the third?

---

### Post by Cheesemill on 2012-05-18
lubuntu-desktop is lubuntu-core plus some extra packages.

For more info see:
[http://packages.ubuntu.com/precise/lubuntu-desktop](http://packages.ubuntu.com/precise/lubuntu-desktop)
[http://packages.ubuntu.com/precise/lubuntu-core](http://packages.ubuntu.com/precise/lubuntu-core)

---

### Post by cshin9 on 2012-05-18
> **Cheesemill said:**
> lubuntu-desktop is lubuntu-core plus some extra packages.

For more info see:
[http://packages.ubuntu.com/precise/lubuntu-desktop](http://packages.ubuntu.com/precise/lubuntu-desktop)
[http://packages.ubuntu.com/precise/lubuntu-core](http://packages.ubuntu.com/precise/lubuntu-core)
Yes, but how will each install options affect functionality? I mean, do I really need lubuntu-desktop or --no-install recommends lubuntu-desktop rather than lubuntu-core?

---

### Post by cshin9 on 2012-09-12
Eh, it's probably better to install ```
lubuntu-desktop --no-install-recommends
```.

---

### Post by mips on 2012-09-13
> **cshin9 said:**
> Yes, but how will each install options affect functionality? I mean, do I really need lubuntu-desktop or --no-install recommends lubuntu-desktop rather than lubuntu-core?

If you run those last two commands in a terminal it will show you what files it will install. It won't do the actual install until you say yes so you can just say no if you don't want to continue.

core installs the least amount of stuff followed by xubuntu-desktop --no-recommends followed by the full lubuntu-desktop.

Easy way to test it is to start by installing core and see how that works for you, if you are not happy do --no-recommends install if you are still not happy do a full install.

---

