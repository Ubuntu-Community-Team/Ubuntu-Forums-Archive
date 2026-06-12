---
title: "How to keep the packages as a backup?"
date: 2011-09-16
forum: New to Ubuntu
---

### Post by sakibmoon on 2011-09-16
The problem is my internet connection is not very fast. So, if I upgrade or install a fresh copy of ubuntu, it is time consuming to install all the softwares again particularly softwares like wine, eclipse, netbeans etc.

I was thinking that if it is possible to keep the backup of the packages. So that I can install from it later. I need idea about how ubuntu manage packages for installing and how can I keep the packages for later use without downloading again.

---

### Post by sanderd17 on 2011-09-16
take a look at apt-on-cd: [http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)

---

### Post by sakibmoon on 2011-09-16
APTonCD looks great. It will help a lot.

I will also appreciate a little insight about packages. Is it possible to keep backup in my hard drive? If so, how can I choose what packages to keep backup?

Say, I have installed Wine on my computer from terminal. It downloaded 77.3 MB of archives. Is it possible to keep backup of those archives.

If I install a fresh copy of Ubuntu, Where do I put those backups so that I can install Wine from terminal without internet connection?

---

### Post by sanderd17 on 2011-09-16
Normally all packages are saved under /var/cache/apt/archives 

But the problem is that those archives become useless when a new version of that program is released.

---

### Post by azertyh on 2011-09-17
hello,
another way : [http://ubuntuforums.org/showthread.php?t=819396](http://ubuntuforums.org/showthread.php?t=819396)

---

