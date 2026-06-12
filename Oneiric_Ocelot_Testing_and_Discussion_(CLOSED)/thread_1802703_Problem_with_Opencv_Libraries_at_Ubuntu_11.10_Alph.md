---
title: "Problem with Opencv Libraries at Ubuntu 11.10 Alpha 2!"
date: 2011-07-12
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by leon.vitanos on 2011-07-12
Hi! At my application i use opencv libraries. So in order to compile it i should install some opencv libraries

 ( SCREENSHOT from my ubuntu 11.04 )

[IMG]http://i55.tinypic.com/rky99c.jpg[/IMG]

I have Ubuntu 11.10 alpha 2 in virtualbox. I tried to install this packages from synaptic there, i left it about 10 minutes and you know the lock screen appeared. But i couldn't write the password ( BUG ) so i powered off the machine while opencv libraries were downloading/installing... After i booted again i complete remove all of opencv libraries i restart and then installed them again. But it is like they are downloaded somewhere so it installes them right away. When trying to execute the command make at my programm's path i have this error: make *** [QOpenCVWidget.o] Error 1

This happens when i don't have the libraries. What should i do? ( Propably the libraries are crashed or something ) :confused:

P.S I don't know if this is the correct section :)

---

### Post by cariboo on 2011-07-12
Packages that are downloaded for installation are stored in /var/cache/apt/archives, you may want to open a terminal and type:

```
sudo apt-get clean
```

to remove all the stored packages, then try to re-install the packages you want.

---

### Post by leon.vitanos on 2011-07-12
> **cariboo907 said:**
> Packages that are downloaded for installation are stored in /var/cache/apt/archives, you may want to open a terminal and type:

```
sudo apt-get clean
```to remove all the stored packages, then try to re-install the packages you want.

Hmm the part that the libraries are downloaded work! But i have the same error.. Anyway i am formating it.. No problem..:D

---

