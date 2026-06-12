---
title: "Error while installing geany"
date: 2010-10-06
forum: Programming Talk
---

### Post by Searock on 2010-10-06
I have recently downloaded geany 0.19.1. 

 [Installation Guide.]("http://www.geany.org/manual/index.html#installation")

 **Autotools based build system**

  The Autotools based build system is very mature and has been well  tested. 
To use it, you just need the Make tool, preferably GNU Make.

  Then run the following commands:[INDENT]>    $ ./configure 
  $ make  [/INDENT]Then as root:[INDENT]   > % make install  [/INDENT]I tried running **./configure** in my terminal and it  ran successfully.

  But when I try running **make** it gives me the this  error.

  > searock@searock-desktop:~/Downloads/geany-0.19.1$ make
make: *** No targets specified and no makefile found.  Stop. Can someone point me in a right direction ?
  Thanks.

---

### Post by kleskjr on 2010-10-06
I would recommend you to install it through synaptic or apt-get. It is safer and updates automatically when there is something new.

write in console:
sudo apt-get install geany

---

### Post by Searock on 2010-10-06
> **kleskjr said:**
> I would recommend you to install it through synaptic or apt-get. It is safer and updates automatically when there is something new.

write in console:
sudo apt-get install geany

Thanks a lot. But what was the problem with make command ?

And what does make actually do ?

---

### Post by spjackson on 2010-10-06
> **Searock said:**
> Thanks a lot. But what was the problem with make command ?

And what does make actually do ?
make compiles an application from source into binary executables, whereas if you install via Synaptic or apt-get then you are installing binaries that have already been compiled for you. Installing from a Ubuntu package is normally the best option, unless you need something vital that is only in the latest source version.

The error you got from make implies that there is neither a file named Makefile nor makefile in your current directory. The ./configure command is supposed to create a Makefile. What did configure create?

```

ls -ltr

```Should show a list files and directories that ends more or less like
```

-rwxr-xr-x 1 spj spj 804320 2010-08-17 15:15 configure
-rw-r--r-- 1 spj spj 161904 2010-08-17 15:53 ChangeLog
-rw-r--r-- 1 spj spj  58358 2010-08-18 18:00 NEWS
drwxr-xr-x 3 spj spj   4096 2010-08-18 18:01 data
-rwxr-xr-x 1 spj spj 219196 2010-10-06 11:23 libtool
-rwxr-xr-x 1 spj spj  41929 2010-10-06 11:23 config.status
-rw-r--r-- 1 spj spj     23 2010-10-06 11:23 stamp-h1
-rw-r--r-- 1 spj spj  30074 2010-10-06 11:23 Makefile
drwxr-xr-x 5 spj spj   4096 2010-10-06 11:23 icons
-rw-r--r-- 1 spj spj   3925 2010-10-06 11:23 geany.spec
-rw-r--r-- 1 spj spj    405 2010-10-06 11:23 geany.pc
drwxr-xr-x 3 spj spj   4096 2010-10-06 11:23 doc
-rw-r--r-- 1 spj spj   4627 2010-10-06 11:23 config.h
-rwxr-xr-x 1 spj spj  30893 2010-10-06 11:23 intltool-update
-rwxr-xr-x 1 spj spj  37500 2010-10-06 11:23 intltool-merge
-rwxr-xr-x 1 spj spj  23044 2010-10-06 11:23 intltool-extract
-rw-r--r-- 1 spj spj  44929 2010-10-06 11:23 config.log

```What do you get?

---

### Post by Searock on 2010-10-06
> **spjackson said:**
> make compiles an application from source into binary executables, whereas if you install via Synaptic or apt-get then you are installing binaries that have already been compiled for you. Installing from a Ubuntu package is normally the best option, unless you need something vital that is only in the latest source version.
............

[/CODE]What do you get?

I don't  know what it has created. But I am sure that makefile or Makefile is not there.

There are similar files like 

> makefile.win32
Makefile.am


Have I downloaded the wrong setup ?

---

### Post by kleskjr on 2010-10-06
hm, I am not an expert but makefile.win32 looks like a windows file. Did you downloaded the right package for Ubuntu?

---

### Post by Zugzwang on 2010-10-06
@OP: Can you post the output of running "./configure" here? Probably some error occurred that prevented it from writing the "Makefile".

---

### Post by Searock on 2010-10-06
> **kleskjr said:**
> hm, I am not an expert but makefile.win32 looks like a windows file. Did you downloaded the right package for Ubuntu?

I have downloaded  [geany-0.19.1.tar.gz]("http://download.geany.org/geany-0.19.1.tar.gz") file from [http://www.geany.org/Download/Releases](http://www.geany.org/Download/Releases)

> **Zugzwang said:**
> @OP: Can you post the output of running "./configure" here? Probably some error occurred that prevented it from writing the "Makefile".

Sure.

> searock@searock-desktop:~/Downloads/geany-0.19.1$ ./configure 
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes

**Some contents removed as it requires a lot of scrolling.**

checking whether binary relocation support should be enabled... no
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for GTK... configure: error: Package requirements (gtk+-2.0 >= 2.8.0) were not met:

No package 'gtk+-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables GTK_CFLAGS
and GTK_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

searock@searock-desktop:~/Downloads/geany-0.19.1$ Even after running ./configure the makefile is still missing.

---

### Post by spjackson on 2010-10-06
> **Searock said:**
> Even after running ./configure the makefile is still missing.
Well yes indeed.
> 
```

checking for GTK... configure: error: Package requirements (gtk+-2.0 >= 2.8.0) were not met:

No package 'gtk+-2.0' found

```configure has told you that it failed, and why.

---

### Post by Searock on 2010-10-06
> **spjackson said:**
> Well yes indeed.
configure has told you that it failed, and why.

Oh, I got it. But then things went well with 

> sudo apt-get install geany

It didn't give me any error while installing it using apt-get.

Is it that ./configure can't find some environment variables?

---

### Post by spjackson on 2010-10-06
> **Searock said:**
> 
It didn't give me any error while installing it using apt-get.

Is it that ./configure can't find some environment variables?
When installing binaries via apt-get, the dependencies are binary libraries. When compiling from source, the dependencies are both binary libraries plus development headers, e.g. you would need to install the package libgtk2.0-dev

---

### Post by Searock on 2010-10-06
[spjackson]("http://ubuntuforums.org/member.php?u=1128302"), [kleskjr]("http://ubuntuforums.org/member.php?u=706724"), [Zugzwang]("http://ubuntuforums.org/member.php?u=403348") thanks a lot, for helping me. :)

---

