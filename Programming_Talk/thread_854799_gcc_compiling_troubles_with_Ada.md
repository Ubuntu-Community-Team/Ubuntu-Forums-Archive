---
title: "gcc compiling troubles with Ada"
date: 2008-07-09
forum: Programming Talk
---

### Post by joesmoe10 on 2008-07-09
Hey I'm trying to use the Asis-tools for Ada but I'm running into trouble.  When I try this command:

```
gnatstub stub.ads
```

I get the following error message

```
gcc: error trying to exec 'gnat1': execvp: No such file or directory
gnatstub: cannot create the tree file for stub.ads
```

I checked to make sure gcc is installed but that's as far as I got.  Any Ideas

---

### Post by LaRoza on 2008-07-09
> **joesmoe10 said:**
> Hey I'm trying to use the Asis-tools for Ada but I'm running into trouble.  When I try this command:

```
gnatstub stub.ads
```

I get the following error message

```
gcc: error trying to exec 'gnat1': execvp: No such file or directory
gnatstub: cannot create the tree file for stub.ads
```

I checked to make sure gcc is installed but that's as far as I got.  Any Ideas

I am not sure what you need, but you will need "build-essential" for gcc. GCC is installed, just barely, you need the rest.

---

### Post by joesmoe10 on 2008-07-10
The build essential package?  Are you sure?  It says:
"If you do not plan to build Debian packages, you don't need this
package.  Moreover this package is not required for building Debian
packages."

I tried it anyway without success.  I think I am missing some component of gcc but I don't know which one.  Do you have any other ideas?

---

### Post by LaRoza on 2008-07-10
> **joesmoe10 said:**
> The build essential package?  Are you sure?  It says:
"If you do not plan to build Debian packages, you don't need this
package.  Moreover this package is not required for building Debian
packages."

I tried it anyway without success.  I think I am missing some component of gcc but I don't know which one.  Do you have any other ideas?

"build-essential" is required to compile any C program with gcc, so it should be installed.

---

### Post by WW on 2008-07-10
[build-essential](http://packages.ubuntu.com/hardy/build-essential) is a "meta-package": it doesn't contain any files itself, but it depends on several other packages, so when you install build-essential, all its dependencies get installed.  The dependencies are: dpkg-dev, g++, gcc, libc6-dev or libc-dev, make.  Each of these depends on additional packages, so by installing build-essential, you end up with everything you need (and more) for compiling C and C++ programs. (Unfortunately, you don't get all the manpages that you might want; somewhere--maybe in the FAQ sticky--there is a list of additional recommended packages to install for manpages.)

---

