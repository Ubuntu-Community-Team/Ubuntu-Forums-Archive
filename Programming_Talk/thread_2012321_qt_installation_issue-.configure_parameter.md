---
title: "qt installation issue-./configure parameter"
date: 2012-06-28
forum: Programming Talk
---

### Post by pellyhawk on 2012-06-28
I downloaded qt-everywhere-opensource-src-4.7.3.tar.gz and hope to configure it. I look up README but still do not know how to set platform and compiler parameter (./configure platform target) and what options the platform and compiler have. Or what is the default value? 

who can clarify it for me? Thanks.

---

### Post by spjackson on 2012-06-30
Just running ./configure should identify the correct platform on Linux. If you run "./configure -h" then the identified platform is shown in brackets in the section for -platform. This will be linux-g++ or linux-g++-32 or linux-g++-64.

The platform is eventually translated to a subdirectory of ./mkspecs so "ls mkspecs" will list the available platforms.

Do you have any special requirements that are likely to need changes to the defaults? If not, I suggest that you just let it do its work.

---

### Post by pellyhawk on 2012-06-30
> **spjackson said:**
> Just running ./configure should identify the correct platform on Linux. If you run "./configure -h" then the identified platform is shown in brackets in the section for -platform. This will be linux-g++ or linux-g++-32 or linux-g++-64.

The platform is eventually translated to a subdirectory of ./mkspecs so "ls mkspecs" will list the available platforms.

Do you have any special requirements that are likely to need changes to the defaults? If not, I suggest that you just let it do its work.

Thanks.

I installed my qt at "/usr/local/Trolltech/Qt-4.7.3-static". But if I run "find / -name mkspecs", I got many results and 2 of them are ```
/usr/share/qt4/mkspecs
/usr/local/Trolltech/Qt-4.7.3-static/mkspecs

```

I "ls mkspecs: at /usr/share/qt4/mkspecs and /usr/local/Trolltech/Qt-4.7.3-static/mkspecs respectively, I notice many platforms are listed including "linux-g++", "linux-g++-32", "linux-g++-64". Do you mean all the platforms(including win32-g++, wince50standard-armv4i-msvc2005 etc) listed  are supported for my ubuntu?

Second, I almost make a mistake. I once specified -platform with "linux32-g++", which do you mean should be "linux-g++-32"?

Finally, if I specify "linux-g++", it means "linux-g++-32" and "linux-g++-64" are support at the same time?

---

### Post by spjackson on 2012-06-30
> **pellyhawk said:**
> Thanks.

I installed my qt at "/usr/local/Trolltech/Qt-4.7.3-static". But if I run "find / -name mkspecs", I got many results and 2 of them are ```
/usr/share/qt4/mkspecs
/usr/local/Trolltech/Qt-4.7.3-static/mkspecs

```
I presume that you already have a Qt development package installed, which is where /usr/share/qt4/mkspecs comes from.

> 
I "ls mkspecs: at /usr/share/qt4/mkspecs and /usr/local/Trolltech/Qt-4.7.3-static/mkspecs respectively, I notice many platforms are listed including "linux-g++", "linux-g++-32", "linux-g++-64". Do you mean all the platforms(including win32-g++, wince50standard-armv4i-msvc2005 etc) listed  are supported for my ubuntu?
No. This is the *everywhere* distribution. That list is essentially all the platforms that Qt supports.

You can only build for targets that you have tools available for. While it is, I understand, possible to cross-compile on Ubuntu for platforms other than Ubuntu, you would need to install appropriate tools, and that's not something I've ever attempted.

> 
Second, I almost make a mistake. I once specified -platform with "linux32-g++", which do you mean should be "linux-g++-32"?

Finally, if I specify "linux-g++", it means "linux-g++-32" and "linux-g++-64" are support at the same time?As I understand it, linux-g++-64 is for building 64-bit on a 64-bit platform. linux-g++-32 is for building 32-bit on a 64-bit platform. linux-g++ is for building 32-bit on a 32-bit platform. I don't know what you would get if you use linux-g++ on a 64-bit Ubuntu, but I don't believe that you will get two builds.

If you want two builds, the normal procedure is to unpack the source, configure for the first build, build, then unpack again into a different directory and configure for the other target.

---

### Post by pellyhawk on 2012-07-01
Many thanks!

> **spjackson said:**
> I presume that you already have a Qt development package installed, which is where /usr/share/qt4/mkspecs comes from.

No. This is the *everywhere* distribution. That list is essentially all the platforms that Qt supports.

You can only build for targets that you have tools available for. While it is, I understand, possible to cross-compile on Ubuntu for platforms other than Ubuntu, you would need to install appropriate tools, and that's not something I've ever attempted.

As I understand it, linux-g++-64 is for building 64-bit on a 64-bit platform. linux-g++-32 is for building 32-bit on a 64-bit platform. linux-g++ is for building 32-bit on a 32-bit platform. I don't know what you would get if you use linux-g++ on a 64-bit Ubuntu, but I don't believe that you will get two builds.

If you want two builds, the normal procedure is to unpack the source, configure for the first build, build, then unpack again into a different directory and configure for the other target.

---

