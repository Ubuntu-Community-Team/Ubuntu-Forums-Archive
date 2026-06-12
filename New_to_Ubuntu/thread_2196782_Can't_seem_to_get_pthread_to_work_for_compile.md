---
title: "Can't seem to get pthread to work for compile"
date: 2013-12-31
forum: New to Ubuntu
---

### Post by kriswilkers on 2013-12-31
Hello, new to Ubuntu (or even any linux) so hopefully someone might know what problem I'm running into :S

I'm trying to use a makefile that requires pthread support, yet everytime I run it I receive the following:

checking for the pthreads library -lpthreads... no
checking whether pthreads work without any flags... no
checking whether pthreads work with -Kthread... no
checking whether pthreads work with -kthread... no
checking for the pthreads library -llthread... no
checking whether pthreads work with -pthread... yes
checking for joinable pthread attribute... PTHREAD_CREATE_JOINABLE
checking if more special flags are required for pthreads... no


My question is I thought pthread support is part of the native linux distro.  Do I have to find the pthread header file or some other system file and install it manually?  Thanks for your help ahead of time, I really appreciate it!

---

### Post by steeldriver on 2013-12-31
Hello and welcome to the forum

AFAIK pthreads development support is provided by the libc6-dev package - however it's not usually necessary to install it manually, it should be brought in as a dependence of the compiler tool chain. How exactly did you install the compiler / build tools? The usually recommended way is to install the build-essential metapackage, either from synaptic / software center or using apt-get

```
sudo apt-get install build-essential
```

That should install gcc, g++, make, and libc6-dev. After that try the ./configure step again and see if it gets any further

---

### Post by damage3025 on 2013-12-31
@kriswilkers

If you are just building some open source package, can you tell exactly which package you are trying to build?

In your snippet, have you noticed the "yes" line?
The detection of pthreads looks successful to me.
You need to understand the fact that pthreads are implemented more or less differently on different operating systems.
Your makefile was just trying many possibilities and found the one that is used by Linux.

---

### Post by kriswilkers on 2013-12-31
Hello Steeldriver, and thanks for your help!

I already followed those steps when I installed for the first time, using the tutorial shown on [https://help.ubuntu.com/community/InstallingCompilers](https://help.ubuntu.com/community/InstallingCompilers)

Ran the ./configure again, same output.

---

### Post by kriswilkers on 2013-12-31
Thanks for your input damage3025

The file I have is just a tarball with a couple accompanying files, makefile, and configure that I receive in an email, not sure if it's up as open source somewhere.  The make was created specifically for unix/linux.  Everything in the make ran through with no problem except for the pthread.

---

### Post by steeldriver on 2013-12-31
Does the ./configure step actually fail to produce a Makefile though? The 'checking' messages in your first post don't necessarily indicate a problem (it is likely search for libpthread**s** on platforms that support the POSIX form and libpthrea**d** on Linux/GNU) - see [http://stackoverflow.com/a/1885953](http://stackoverflow.com/a/1885953) for example

---

