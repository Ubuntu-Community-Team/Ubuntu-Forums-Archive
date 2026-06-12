---
title: "C library documentation manager"
date: 2008-10-08
forum: Programming Talk
---

### Post by kulkarniniraj on 2008-10-08
hello
   I have been using 'tc' in windows for c programming
just now i have shifted to ubuntu.
Now i want to know if there is any good help manager for gcc library documentation.
I think gcc library documentation is in package glibc & is installed in folder /usr/share/doc/glibc
tell me if i am wrong. The help here are not organized by header file & it's functions so tell me where i can get help in such format

---

### Post by dwhitney67 on 2008-10-08
You can try using the man-pages.  To get them:
```
sudo apt-get install manpages-devel
```

Then you should be able to get information, say on fopen(), using the following command:
```
man fopen
```

If you have questions on how to use 'man':
```
man man
```

Here's the Wiki on Man-Pages:  [http://en.wikipedia.org/wiki/Man_page](http://en.wikipedia.org/wiki/Man_page)

---

### Post by kostkon on 2008-10-08
You can install the [*glibc-doc*]("http://packages.ubuntu.com/hardy/glibc-doc") package and [*devhelp*]("http://packages.ubuntu.com/hardy/devhelp") to view it. *Devhelp* is a useful documentation browser.

---

