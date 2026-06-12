---
title: "Using GCC 4.2"
date: 2007-11-30
forum: Programming Talk
---

### Post by CodeWarMonkey on 2007-11-30
I am using Feisty Fawn and want to use gcc 4.2. If I install gcc, it will automatically install gcc 4.1 I want to use gcc 4.2 because 4.2 has features that 4.1 are missing. Is there a good way to make gcc point to 4.2 instead of 4.1, or do I have to manually change the symbolic links in /usr/bin?

Thanks.

---

### Post by aks44 on 2007-11-30
AFAIK there is no Feisty backport for GCC 4.2. Which means you probably shouldn't try to install it.

If you really need 4.2 features you'd be better off upgrading to Gutsy.

Anyway as far as the C++ standard goes I'm not aware of any improvements, or are you relying on vendor-specific features?

---

### Post by CodeWarMonkey on 2007-11-30
My mistake. I am using Gutsy. I am creating a toolchain for a cross-compiler. gcc 4.2 is required  for the --sysroot option. I want to be able to move my cross-compiler out the staging directory into the appropriate spot (/usr/local/comp).

---

### Post by samjh on 2007-12-01
If you've already installed the package, trying using sudo update-alternatives to change gcc.

Sorry, I'm in a rush, try the --help option about update-alternatives.

---

### Post by TwoWordz on 2008-01-10
Hi, 

I'm looking for the correct way to change the gcc compiler on a ubuntu system. I tried update-alternatives:

```

root@newcomputer:~# update-alternatives --list gcc
No alternatives for gcc.

```

and I found this bug report:

[https://bugs.launchpad.net/ubuntu/+source/gcc-4.2/+bug/145486](https://bugs.launchpad.net/ubuntu/+source/gcc-4.2/+bug/145486)

This answer states that it is not an alternative (or a bug):

> 
GCC versions come with different ABIs and APIs, therefore it is not an alternative. If you do want to use a different version do so by building witj CC=gcc-X.Y CXX=g++-X.Y


Using CC=gcc-4.2 is ok, but I wanna make it the default compiler on the system. Can it break anything?

Is a symlink the right way to do it?

Thanks,

TW

---

### Post by TwoWordz on 2008-01-13
bump?

---

