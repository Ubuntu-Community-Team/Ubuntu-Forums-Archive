---
title: "Installing my first program"
date: 2012-02-16
forum: New to Ubuntu
---

### Post by Nicky1204 on 2012-02-16
I'm very new to Ubuntu, and I'm trying to compile my first program. To do so, I've been following this guide:

[http://www.makeuseof.com/tag/compile-install-tar-gz-tar-bz2-files-ubuntu-linux/](http://www.makeuseof.com/tag/compile-install-tar-gz-tar-bz2-files-ubuntu-linux/)


After hours of Googling, I think its finally time to make a thread for some help.

It has been going well, until I get the step when I run ./configure and it checks for all of the necessary packages to compile the program.  After running the command, I'm greeted by this:


checking for DEPS... configure: error: Package requirements (
    gconf-2.0 >= 2.18.0,
    libwnck-1.0 >= 2.18.0
) were not met:

No package 'libwnck-1.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables DEPS_CFLAGS
and DEPS_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.


The guide says to search for it by the file name, so run:
apt-file search libwnck-1.0I'm given a long list of information and files, and I'm unsure what I'm supposed to install, and how. If it helps, I'm trying to install Simdock.


Edit: I'm using Ubuntu 11.04

---

### Post by wolfen69 on 2012-02-16
Search *Synaptic Package Manager* for the files you need, install them, and try again to compile.

---

### Post by Scott Baker on 2012-02-16
I would like some clarification please. You are trying to install simdock by compiling your own program? In your version of Ubuntu, simdock can be found in the synaptic package manager. Open that, put the word "simdock" in the search location, and it will come up in a few seconds. When you find it, just put a tick mark next to it (mark for installation), then continue the install as you would with any other application. Good luck.  [-o<

Just saw your version correction. Simdock is available through the software center. Install, log out, log back in, and it will be ready to use.

---

### Post by wolfen69 on 2012-02-16
> **Scott Baker said:**
> I would like some clarification please. You are trying to install simdock by compiling your own program? In your version of Ubuntu, simdock can be found in the synaptic package manager. Open that, put the word "simdock" in the search location, and it will come up in a few seconds. When you find it, just put a tick mark next to it (mark for installation), then continue the install as you would with any other application. Good luck.  [-o<

I was under the impression that the OP was just trying to compile because he *wanted* to. (which is OK) But who knows.

---

### Post by Nicky1204 on 2012-02-17
> **wolfen69 said:**
> I was under the impression that the OP was just trying to compile because he *wanted* to. (which is OK) But who knows.


Yes, you're correct. I just chose this as a program to compile myself because I wanted to, however if I'm unable to I'll just install it through the package manager.

---

