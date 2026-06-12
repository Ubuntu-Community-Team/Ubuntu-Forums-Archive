---
title: "create deb from c++"
date: 2006-12-31
forum: Packaging and Compiling Programs
---

### Post by Kiwinote on 2006-12-31
I have been writing a c++ program that is in one file, program.cpp. Now i would like to create a deb from it. Could anyone tell me how to do this?

---

### Post by Lord Illidan on 2006-12-31
Never done it myself, but google found this link

[http://blog.mypapit.net/2006/02/create-you-own-debianubuntu-deb-package.html](http://blog.mypapit.net/2006/02/create-you-own-debianubuntu-deb-package.html)

---

### Post by po0f on 2006-12-31
Kiwinote,

If it's just one file, why not distribute the source?  Compiling one file isn't that hard, even for an absolute beginner, it's just a matter of cut-and-paste.

---

### Post by Kiwinote on 2006-12-31
The reason why I don't want to do that is because in the future it will grow to a number of files. On the other side it isn't a bad idea to know how to make debs.

---

### Post by Kiwinote on 2006-12-31
I have tried out that tutorial now, and it seems as if I have to write my own makefile...
any ideas?

---

### Post by Kiwinote on 2006-12-31
ok, created a makefile by now and got a lot further. The following error occurs when I do "debuild -us -uc"
> tar: -: file name read contains nul character
dpkg-deb: building package `testprog' in `../testprog_1.0.0_all.deb'.
 dpkg-genchanges
dpkg-genchanges: error: badly formed line in files list file, line 1

---

### Post by Kiwinote on 2006-12-31
Problems solved, in the meantime anyway :)

---

### Post by neurostu on 2008-06-05
How did you solve the :
dpkg-genchanges: error: badly formed line in files list file, line 1 

error?

---

### Post by neurostu on 2009-06-02
I figured out that I was getting the error because of a bad section field under debian/control

---

