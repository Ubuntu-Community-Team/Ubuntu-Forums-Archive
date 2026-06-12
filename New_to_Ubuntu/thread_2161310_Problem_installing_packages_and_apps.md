---
title: "Problem installing packages and apps"
date: 2013-07-10
forum: New to Ubuntu
---

### Post by LinuxUser666 on 2013-07-10
Hello fellow Ubuntu users, I am using Ubuntu 12.04 with GNOME DE. I seem to have a problem lately...you see whenever I try to use an apt to download and install something, for instance alien with:
```
sudo apt-get install alien
```
and get result like this:
```
Media change: please insert the disc labeled 'Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release i386 (20120817.3)'
in the drive '/cdrom/' and press enter

```
I do that, put the CD in the drive but nothing is happening. Can someone please explain what is it all about and how to fix it? 

Thank you, stay brutal. :biggrin:

---

### Post by CatKiller on 2013-07-10
If you have an Internet connection, you don't want to use the cd as a repository. Disable it in Software Sources, or remove that line from sources.list.

---

### Post by LinuxUser666 on 2013-07-15
Ok I did that, removed my cd from repository lists and I am all clear now. 

Thanks for the tip, stay brutal, my regards.  :-D

---

