---
title: "Issues packaging Qt5 project"
date: 2017-02-23
forum: Packaging and Compiling Programs
---

### Post by 3vi1 on 2017-02-23
I have a Linux/Windows project that I created with Qt Creator that I'm now trying to package for my Ubuntu PPA.  Unfortunately, this is my first experience packaging for Linux, and the issues I'm having don't seem to be covered in any of the online walk-through/tutorials I've read as of yet.  I'm hoping the gurus here can nudge me in the right direction.

1.  [I get a complaint when debuild tries the 'make distclean' step]("http://pastebin.com/mGbTvWQK").  I do not get this complaint if I run qmake first, such that there is a makefile in the current directory... however a lot of the tutorials said I should only need my .pro file to exist and that the makefile should be cleaned up along with the object files when preparing the directory.  Is this solely cosmetic, or is it a real issue?

2.  My project seems to depend on qt5-default to build.  From what I've read at [https://pkg-kde.alioth.debian.org/packagingqtbasedstuff.html](https://pkg-kde.alioth.debian.org/packagingqtbasedstuff.html), I shouldn't actually be adding that to the depends.  I added QT_SELECT=5 to my debian/rules file, but I'm not sure which 'tool' they refer to when they say "Call the tool using the '-qtx' parameter, where x can be replaced with any of the options above."

3.  With qt5-default in the build depends anyway, things seem to proceed well until,  [qmake throws an error as if it were called with bad parameters during the pbuilder build]("http://pastebin.com/dCtGYJFp").

I've probably been fighting with this and reading obsolete tutorials for 7 hours now... any insight is appreciated.

---

