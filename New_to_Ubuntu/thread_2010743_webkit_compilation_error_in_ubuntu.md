---
title: "webkit compilation error in ubuntu"
date: 2012-06-26
forum: New to Ubuntu
---

### Post by arpitjain on 2012-06-26
I am new to Webkit and Ubuntu. I am following instructions to install webkit from the following page : [https://help.ubuntu.com/community/WebKit#Compile_the_code](https://help.ubuntu.com/community/WebKit#Compile_the_code)

and getting the following error after "make" command:

make[1]: Entering directory `/home/arpit/opensource/Webkit/SourceZip/webkit'
/bin/mkdir -p ./.deps/DerivedSources
  CXX    Source/WebCore/platform/network/soup/libWebCore_la-CookieJarSoup.lo
In file included from Source/WebCore/platform/network/soup/CookieJarSoup.cpp:22:0:
Source/WebCore/platform/network/soup/CookieJarSoup.h:31:26: fatal error: libsoup/soup.h: No such file or directory
compilation terminated.
make[1]: *** [Source/WebCore/platform/network/soup/libWebCore_la-CookieJarSoup.lo] Error 1
make[1]: Leaving directory `/home/arpit/opensource/Webkit/SourceZip/webkit'
make: *** [all] Error 2

can anyone help?

---

### Post by MG&amp;TL on 2012-06-26
Do you have a reason for manual compilation? There's several webkit packages in the Ubuntu repos now, and that page looks a bit...outdated.

Anyway, it looks like you need libsoup.

```
sudo apt-get install libsoup2.4-dev
```

---

### Post by arpitjain on 2012-06-26
i am installing manually because i want the source code... and i already have lipsoup installed!

---

### Post by MG&amp;TL on 2012-06-26
> **arpitjain said:**
> i am installing manually because i want the source code... and i already have lipsoup installed!

...you've already got the source code. Why do you need to compile? 

Okay, post output of:
```
apt-cache policy libsoup2.4-dev
```

...just making sure before we go down the header-file debugging route....

---

### Post by arpitjain on 2012-06-26
libsoup2.4-dev:
  Installed: 2.38.1-1
  Candidate: 2.38.1-1
  Version table:
 *** 2.38.1-1 0
        500 [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) precise/main i386 Packages
        100 /var/lib/dpkg/status

---

### Post by MG&amp;TL on 2012-06-26
Okay, so it should be there, but it's not finding it.

Post output of:

```
 ls /usr/include/libsoup-2.4/libsoup/ | grep "soup.h"

```

please. :)

---

### Post by arpitjain on 2012-06-27
soup.h
soup-headers.h

---

### Post by MG&amp;TL on 2012-06-27
Sorry, no idea then. I have a feeling /usr/include/libsoup-2.4/ isn't being included in the header file search path, but I haven't got enough experience with autoconf to tell you how to change that.

Suggestions:

-wait around until someone gifted with autoconf turns up.

-Try updating the source tree: maybe it's a temporary glitch:

```
svn up
```

-Report a bug on the project page, and see what they say.

---

