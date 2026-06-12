---
title: "How to install DB2 a step by step"
date: 2008-06-24
forum: New to Ubuntu
---

### Post by sivhaga on 2008-06-24
Hi everyone,

Im trying to Install DB2 for Linux on Ubuntu.
I was told to install two prequisite deb files before installing DB2.

This is what i did so far:
dpkg –install libstdc++5_3.3.6-13ubuntu2_i386.deb
dpkg –install libaio-dev_0.3.106-5ubuntu2_i386.deb

The problem now it is when i try to do this:
 tar -xvzf db2exc_950_LNX_x86.tar.gz

It runs but gives me this error at last says " tar: Error exit delayed from previous errors"

Then when i try to check up there about the tar error it shows that there were errors when it was busy loading which are : 
"Cannot create symlink to 'libinpro.so.1':Operation not permitted"
"Cannot create symlink to 'libdb2glln install.so.1':Operation not permitted"

Please try to help me out and if possible, can you provide me with a step by step on how to install DB2 on Linux

---

### Post by Nepherte on 2008-06-24
[http://ubuntuguide.org/wiki/Ubuntu:Gutsy#IBM_DB2](http://ubuntuguide.org/wiki/Ubuntu:Gutsy#IBM_DB2)

---

