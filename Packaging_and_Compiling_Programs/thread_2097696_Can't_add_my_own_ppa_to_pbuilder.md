---
title: "Can't add my own ppa to pbuilder"
date: 2012-12-24
forum: Packaging and Compiling Programs
---

### Post by FSMaximeH on 2012-12-24
Hello all,

I try to package my own app. I use pbuilder to check the compilation. I have a problem related to libs stored on my own ppa:
This apps needs a lib (to work) and a lib-dev (to compile) that is stored on my own ppa

**First i use**
```

sudo pbuilder update --override-config  --othermirror "deb http://ppa.launchpad.net/maxime-haselbauer/wotan/ubuntu precise main"

```To add my ppa to the source of pbuilder,but inside the output I find a 
```

W: GPG error: http://ppa.launchpad.net precise Release: The following signatures couldn't be verified because the public key is not available:

```When I then try to
```

sudo pbuilder --extrapackages  libname-of-my-lib-dev

```he says he is unable to locate the package


**Secont try I have made is**
```

sudo pbuilder update --override-config  --othermirror "deb http://ppa.launchpad.net/maxime-haselbauer/wotan/ubuntu precise main" --extrapackages libcopy-playlist-backend-dev

```it looks like it found the packages, but saying
```

WARNING: The following packages cannot be authenticated!
  libcopy-playlist-backend libcopy-playlist-backend-dev
E: There are problems and -y was used without --force-yes

```if launch
```

sudo pbuilder build *.dsc

```right after this, he will say that my lib (libcopy-playlist-backend-dev) is not installable.....


**By the way,**
it also keeps saying 
```

W: /home/max/.pbuilderrc does not exist

```each time I launch a pbuilder command<= WTF ?


Anyhelp is  welcome. It is almost the first time I package an application and it is all very abstruse to me 

And merry christmas by the way !

---

### Post by FSMaximeH on 2012-12-26
uping

---

### Post by FSMaximeH on 2013-01-03
Super up :p

---

### Post by akshay.bhardwaj on 2013-01-04
Hi,

There seems to be signing problem with ur ppa while installing that could be fixed with [https://wiki.ubuntu.com/PbuilderHowto#Signing_Source_Files](https://wiki.ubuntu.com/PbuilderHowto#Signing_Source_Files).
Further you can check about using pbuilder in more details at [https://wiki.ubuntu.com/PbuilderHowto](https://wiki.ubuntu.com/PbuilderHowto) or [http://www.debian-administration.org/?article=114](http://www.debian-administration.org/?article=114)

---

