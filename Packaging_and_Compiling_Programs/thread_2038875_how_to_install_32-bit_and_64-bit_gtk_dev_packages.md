---
title: "how to install 32-bit and 64-bit gtk dev packages?"
date: 2012-08-07
forum: Packaging and Compiling Programs
---

### Post by dragon512 on 2012-08-07
Hello,

I trying to compile on the same system a 32-bit and 64-bit gtk program. The issue I am having is that when I try to do something like:

sudo apt-get install libglib2.0-dev libglib2.0-dev:i386 

I get a message like this:

The following packages have unmet dependencies:
 libglib2.0-dev : Conflicts: libglib2.0-dev:i386 but 2.32.3-0ubuntu1 is to be installed
 libglib2.0-dev:i386 : Depends: libpcre3-dev:i386 (>= 8.11) but it is not going to be installed
                       Conflicts: libglib2.0-dev but 2.32.3-0ubuntu1 is to be installed
E: Unable to correct problems, you have held broken packages.


I don't get it, I thought the whole point of multiarch was to allow this to happen without issue.

is it not possible to install native and cross platform libraries  on ubuntu 12.04, and if so (as I really hope it is) how do you do it?

Thanks!

---

### Post by dragon512 on 2012-08-08
I have been looking in to this more. Its seems this is not possible. It seems that it is a issue with how packages are made on Ubuntu. for example I can go to a Fedora 17 system a say

yum install glib-devel.i686 glib-devel.x86_64

and this works fine. the same command on ubuntu:

apt-get install libglib2.0-dev libglib2.0-dev:i686

fails with a message like I reported before.:(

---

