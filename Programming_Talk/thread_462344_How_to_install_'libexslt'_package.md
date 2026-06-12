---
title: "How to install 'libexslt' package?"
date: 2007-06-02
forum: Programming Talk
---

### Post by yinglcs2 on 2007-06-02
Hi,

I run './configure' on swfmill, but I get the following error. Can you please tell me how can I find the libexslt library?

checking for XSLT... configure: error: Package requirements (libexslt) were not met:

No package 'libexslt' found

I have tried this, but that does not solve my problem:
$ sudo apt-get install libexslt*
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libexslt*



Thank you.

---

### Post by GeneralZod on 2007-06-02
Have you tried

```

sudo apt-get install libxslt1-dev

```

---

### Post by WW on 2007-06-02
Install the package **libxslt1-dev**.

I found this by searching for **xslt** at packages.ubuntu.com.  The search finds many packages, but most are obviously related to ruby or python or some other software.  The most likely candidate was **libxslt1.1**; to be sure, I checked the list of files that are installed by the package, and found that it installs the file /usr/lib/libexslt.so.0, which is the shared library.  Since you are trying to compile a program that uses this library, you will probably need the -dev version, which is **libxslt1-dev**.  It depends on **libxslt1.1**, so you will also get that when you install the -dev version.

---

### Post by yinglcs2 on 2007-06-02
Thanks.  That solves my problem.


But I have a new one now. I get this:

      WARNING: You need to have the Ming development and utilities packages
                 installed to run most of the tests in Gnash testsuite.
                 Install it from [http://ming.sourceforge.net](http://ming.sourceforge.net)
                 or .deb users: apt-get install libming-dev

but I think I have already install libming-dev , can you please tell me how to solve my problem?

$ sudo apt-get install libming-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libming-dev is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 29 not upgraded.


Thank you.

---

### Post by GeneralZod on 2007-06-02
```
sudo apt-get install libming-util
```

?

---

### Post by yinglcs2 on 2007-06-02
Thanks. I tried it.

$ sudo apt-get install libming-util-dev
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libming-util-dev
scheung@scheung-laptop:bin$ sudo apt-get install libming-util
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libming-util is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 29 not upgraded.


But it still does not work:

      WARNING: You need to have the Ming development and utilities packages
                 installed to run most of the tests in Gnash testsuite.
                 Install it from [http://ming.sourceforge.net](http://ming.sourceforge.net)
                 or .deb users: apt-get install libming-dev

---

### Post by ctult on 2009-11-14
Just type
```
sudo apt-get install libming-dev
```

---

