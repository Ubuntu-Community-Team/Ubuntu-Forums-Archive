---
title: "[SOLVED] reconstructor"
date: 2008-07-12
forum: New to Ubuntu
---

### Post by AnLGP on 2008-07-12
I can't get this to work.  I run it and this comes out

steve@ubuntu:~/Desktop/reconstructor$ sudo python reconstructor.py
[sudo] password for steve: 
No module named glade
steve@ubuntu:~/Desktop/reconstructor$ 

I installed glade after that popped up the first time and when I "ls" the directory 

credits.txt  known_issues.txt  lib          modules     reconstructor.py
glade        lang              license.txt  readme.txt

that's what I get.  What gives?

---

### Post by red_team316 on 2008-07-13
sudo apt-get install python-glade(check the package name)

---

### Post by AnLGP on 2008-07-13
steve@ubuntu:~$ sudo apt-get install python-glade
[sudo] password for steve: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package python-glade is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package python-glade has no installation candidate

--

I just checked and I have python-glade2 installed

---

### Post by red_team316 on 2008-07-13
sudo apt-get install squashfs-tools make gcc mkisofs rsync libbogl-dev libusplash-dev gpg dpkg-dev fakeroot apt-utils python python-gtk2 python-glade2

[http://reconstructor.wiki.sourceforge.net/UsingReconstructor](http://reconstructor.wiki.sourceforge.net/UsingReconstructor)

It's one of those. I had this problem a long time ago as some of the dependancies aren't installed by default in kubuntu.

---

### Post by AnLGP on 2008-07-13
steve@ubuntu:~$ sudo apt-get install squashfs-tools make gcc mkisofs rsync libbogl-dev libusplash-dev gpg dpkg-dev fakeroot apt-utils python python-gtk2 python-glade2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
squashfs-tools is already the newest version.
make is already the newest version.
gcc is already the newest version.
Note, selecting genisoimage instead of mkisofs
genisoimage is already the newest version.
rsync is already the newest version.
libbogl-dev is already the newest version.
E: Couldn't find package gpg

---

### Post by red_team316 on 2008-07-13
get rid of the gpg. the package has probably changed too and you probably already have it. try the python-gtk2 and restart reconstructor.

---

### Post by AnLGP on 2008-07-13
got it

---

