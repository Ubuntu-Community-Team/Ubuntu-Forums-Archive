---
title: "uninstalling programs in synaptic package manager"
date: 2008-06-12
forum: New to Ubuntu
---

### Post by Troca on 2008-06-12
hi iam still new to Ubuntu and as a n00b i like trying new programs and stuff, 99.9% of the times i install a program i use synaptic package manager and sometimes programs dosent work 100% prop sens i use 64bit version :p and sometimes i just don't like the program. so i just start synaptic package manager again search for the program and uninstall it now what i noticed is that it dosent uninstall all the Dependant packages that it sometimes install for some programs my question will this slow down my computer ?

---

### Post by dje on 2008-06-12
in synaptic if you mark the package for complete removal instead of just removal it will also remove dependencies ;) extra dependencies will just take up hard disk space not memory

---

### Post by bruce89 on 2008-06-12
APT has never removed depenant packages, hence my exculsive use of aptitude.

---

### Post by Troca on 2008-06-12
yeah i started doing that latley. thanks alot for the reply. and for programs i havent done that on will those slow down my system you think ?

---

### Post by gr4nf on 2008-06-12
I doubt it. To clean up your system, you should occasionally run:
```

sudo apt-get clean
sudo apt-get autoremove

```

---

### Post by Troca on 2008-06-12
> **gr4nf said:**
> I doubt it. To clean up your system, you should occasionally run:
```

sudo apt-get clean
sudo apt-get autoremove

```

thank alot for that info really good to know :) thank you

---

### Post by bruce89 on 2008-06-12
> **Troca said:**
> and for programs i havent done that on will those slow down my system you think ?

No, just a waste of HD space.

---

### Post by nimroad on 2009-09-16
> **gr4nf said:**
> I doubt it. To clean up your system, you should occasionally run:
```

sudo apt-get clean
sudo apt-get autoremove

```

Great tip

Thanks

---

### Post by bbbenjy on 2009-09-16
> **bruce89 said:**
> No, just a waste of HD space.
try :sudo apt-get autoremove

:P testing foruns reply :(

---

