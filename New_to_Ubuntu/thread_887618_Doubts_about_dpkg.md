---
title: "Doubts about dpkg"
date: 2008-08-12
forum: New to Ubuntu
---

### Post by 7raTEYdCql on 2008-08-12
Had some doubts about dpkg.

1)What is the difference between depg and dpkg-deb.

2)Someone told me that installing all the files in the directory by using the command dpkg -i *.deb is not a wise idea. Why? Instead he suggested that i use the following
```
dpkg --unpack --configure -G -a
```. Any reason.

3)I am a noob in Linux and am readig the man pages to get things straight. What do you mean by configuring a package.


Any help???

---

### Post by OffAxis on 2008-08-12
> 1)What is the difference between depg and dpkg-deb.
I'm guessing you mean dpkg and dpkg-deb...

dpkg-deb only packs, unpacks, and gives info about a package. dpkg can install, configure, and remove packages (among other things). It's 'built on' dpkg-deb in so much that it calls dpkg-deb when it's asked to pack, unpack, or give info on a package.

> 2)Someone told me that installing all the files in the directory by using the command dpkg -i *.deb is not a wise idea. Why?Instead he suggested...
Installing like that checks the versions and won't install an older version on top of a new one. I've always installed manually with just dpkg -i and never had a problem.

> 3)I am a noob in Linux and am readig the man pages to get things straight. What do you mean by configuring a package.
Configuring a package means setting up the options for it. Things like screen resolution, system architecture, etc. Generally it's automated, but sometimes you'll be prompted to input information.

---

### Post by sayakb on 2008-08-12
dpkg -i *.deb should work fine, unless there are multiple versions of the same package. For example, copying one's apt cache to someone else's machine may copy the packages of applications of older plus updated versions. Firing dpkg -i *.deb may break the system.

---

