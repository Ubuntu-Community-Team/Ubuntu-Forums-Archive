---
title: "Executable binary is now shared library"
date: 2016-10-29
forum: Packaging and Compiling Programs
---

### Post by hainsvdbosch on 2016-10-29
With Ubuntu 16.10 i have a problem.When compiling something, the executable binary is showed as shared-library in Nautilus.

This is with a simple c++ program, but also with FFmpeg, Audacity and GIMP.

I have no errors during compiling and installing.

The binary has the right size,location(usr/local/bin) and name.But i can't doubleclick(error: there is no application installed for shared library).

Launch from shell doesn't work also due to missing other shared libraries.

I rebuild everthing from stratch without errors(but a lot more warnings btw). 

With Ubuntu 16.04 it was no problem. I could copy the binary to my desktop, make icon, double click on it and so on.

I guess it has something to do with the newer gcc/g++.

What's wrong?

---

### Post by Danfun64 on 2016-11-05
I have a similar program. Compile software results in it being viewed as a "shared binary", although in my case launching the software from the terminal works. How do I fix this issue?

Note: I am running Xubuntu 16.10 64-bit which was upgraded from 16.04, and instead of Nautilus I am having the problem with Thunar.

---

### Post by hainsvdbosch on 2016-11-06
[https://bugs.launchpad.net/ubuntu/+source/gcc-defaults/+bug/1639531](https://bugs.launchpad.net/ubuntu/+source/gcc-defaults/+bug/1639531) 
(Thanks for reporting Olathe)

Now just wait....:popcorn:


Update: All programs running now..But via terminal only.

---

### Post by mc4man on 2016-11-07
Nothing new, happens to some 64 bit exec.. binaries. (and of no real issue at all in terms of binary running except from file-manager
Read thru this thread from 3 yrs. ago if desired
[http://mplayerhq.hu/pipermail/mplayer-users/2013-October/086734.html](http://mplayerhq.hu/pipermail/mplayer-users/2013-October/086734.html)

edit: if there is a bug likely with the file managers/mime magic, ect..

---

### Post by Le Gluon du Net on 2016-11-11
Same bug for me, all my compilations executables seen as shared library in Nautilus or Thunar since I upgraded to Ubuntu 16.10.

---

