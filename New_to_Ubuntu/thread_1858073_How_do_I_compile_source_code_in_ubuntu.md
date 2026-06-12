---
title: "How do I compile source code in ubuntu?"
date: 2011-10-11
forum: New to Ubuntu
---

### Post by computerguts on 2011-10-11
I know this is a stupid question, its been a while since I have used ubuntu and am trying to get back to using it again. How do I compile souce code? 
 
Thanks for your help in advance

---

### Post by Lisiano on 2011-10-11
```
make
```
If you need to configure it, run this before make
```
./configure
```
To install
```
sudo make install
```

---

### Post by anewguy on 2011-10-11
Do you mean your own source code, or do you mean a package you downloaded that is source code?

The first thing would to be sure the build-essential package is installed, either via apt-get or via the synaptic package manager.  This includes various headers, the gcc compiler, etc..  This also covers C and C++.

Let's go with the easiest scenario first:

- you downloaded a package and it contains source code you must compile

Normally such packages include a README type file that will have the specific instructions.  The normal procedure is to do the following:

- configure (usually done via ./configure when at the top-level folder containing the package folders)

- make

- sudo make install


Now for the 2nd option - your own source code.  There are various IDE's available - just my personal preference is code:blocks.  If you aren't into IDE's then you would need to know the paths of extra libs, etc., and use your own gcc or g++ command line to compile.

For other languages I'm sure the procedure is similar - I only use C so I don't know what's available for other languages.

Dave ;)

---

### Post by oldos2er on 2011-10-11
[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

[https://help.ubuntu.com/community/CompilingSoftware](https://help.ubuntu.com/community/CompilingSoftware)

---

