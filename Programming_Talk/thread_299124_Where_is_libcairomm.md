---
title: "Where is libcairomm"
date: 2006-11-13
forum: Programming Talk
---

### Post by gareththegeek on 2006-11-13
Hi,

I am trying to use cairomm in my code to do a little line drawing for a hangman game I'm writing using c++ and libglademm but it doesn't appear to be installed.  Searching Synaptic I can't find libcairomm.

I tried downloading the packages from:
[http://packages.debian.org/testing/libs/libcairomm-1.0-0](http://packages.debian.org/testing/libs/libcairomm-1.0-0)
[http://packages.debian.org/testing/libdevel/libcairomm-1.0-dev](http://packages.debian.org/testing/libdevel/libcairomm-1.0-dev)

but I get:

gareth@gareth-desktop:~/Downloads$ sudo dpkg -i libcairomm-1.0-0*.deb
Selecting previously deselected package libcairomm-1.0-0.
(Reading database ... 127656 files and directories currently installed.)
Unpacking libcairomm-1.0-0 (from libcairomm-1.0-0_0.6.0-4_i386.deb) ...
dpkg: dependency problems prevent configuration of libcairomm-1.0-0:
 libcairomm-1.0-0 depends on libc6 (>= 2.3.6-6); however:
  Version of libc6 on system is 2.3.6-0ubuntu20.
 libcairomm-1.0-0 depends on libcairo2 (>= 1.2.0); however:
  Version of libcairo2 on system is 1.0.4-0ubuntu1.
dpkg: error processing libcairomm-1.0-0 (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libcairomm-1.0-0

Should I go ahead and try and get these new versions of libc and libcairo or am I missing something.  I don't wanna bugger my system up :D

Thanks
G!

---

### Post by hod139 on 2006-11-13
It looks like it is in edgy ([http://packages.ubuntu.com/edgy/source/cairomm)](http://packages.ubuntu.com/edgy/source/cairomm)).  I would not suggest trying to install the debian versions on your machine.  You might be able to download the ubuntu source package and build on your machine, but chances are with that dependency on libcairo that won't work.  You may have to upgrade to edgy or try googling for a dapper version.

---

### Post by llonesmiz on 2006-11-14
You need to install libcairomm-1.0-dev:

sudo apt-get install libcairomm-1.0-dev

it's in main so if you can't install it you probably have a problem with your repositories.
I suggest you install libcairomm-1.0-doc too. This way you'll be able to look up any function name using devhelp.

---

### Post by gareththegeek on 2006-11-15
Thanks for the help, tried to install it as suggested

gareth@gareth-desktop:~$ sudo apt-get install libcairomm-1.0-dev
Password:
Reading package lists... Done
Building dependency tree... Done
Package libcairomm-1.0-dev is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libcairomm-1.0-dev has no installation candidate

Tried installing the packages from packages.ubuntu.com but got similar errors to my first post when using the debian versions. e.g. libc etc is too old.

Any other ideas?  Or is there something I can use instead of cairo for line drawing etc?

Thanks,
G!

---

### Post by hod139 on 2006-11-15
If you want to use libcairomm in ubuntu, my guess (just a guess) is that you will have to upgrade to edgy (6.10).  I'm not sure about an alternative.

---

### Post by llonesmiz on 2006-11-15
I think some people have had problems installing libcairo-dev when they are using external repositories, especially for compiz/beryl. If that is not your case I can't think of what may be the problem.

---

### Post by gareththegeek on 2006-11-15
Hi,

I am only using the Ubuntu repositories and searching Synaptic doesn't show up anything for libcairomm, just libcairo. :(

Thanks,
G!

---

