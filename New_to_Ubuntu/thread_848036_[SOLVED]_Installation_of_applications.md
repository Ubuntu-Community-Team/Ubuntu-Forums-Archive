---
title: "[SOLVED] Installation of applications"
date: 2008-07-03
forum: New to Ubuntu
---

### Post by wabbit46 on 2008-07-03
I do not have an Internet connection on my Ubuntu computer and downloaded a program using Windows and burnt it to CD.

Synaptic refuses to recognise the program. Package installer claims it has unsatisfiable dependencies (which it does not have). I would like to try installing it with aptitude but cant find a location to place it where aptitude will find it.

Can anyone advise me where to place it so that aptitude can find it or any other  suggestions as to how to install it. I am using Ubuntu version 8.04 LTS Desktop.

---

### Post by sharks on 2008-07-03
If it asks for dependencies , it will give some names (mostly lib files). download those lib files and install it.

---

### Post by mcduck on 2008-07-03
Synaptic, Aptitude and apt-get are only used to install packages from Ubuntu's repositories. If you  already have the packages on your system, the tool used for installing them is dpkg.

For example:
```
sudo dpkg -i /path/to/package1.deb /ppath/to/package2.deb
```

---

### Post by ChameleonDave on 2008-07-03
> **wabbit46 said:**
> I do not have an Internet connection on my Ubuntu computer and downloaded a program using Windows and burnt it to CD.

Why so cryptic?

If you tell us what program it is, we can give more specific advice.

---

