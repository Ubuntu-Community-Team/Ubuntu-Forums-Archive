---
title: "is gtkmm cross platform?"
date: 2017-06-29
forum: Programming Talk
---

### Post by rockandsalt on 2017-06-29
I know gkt+ is cross-platform. But on the gktmm website all the download link they have are for linux system. So it made me wonder if gtkmm is actually cross platform. By cross platform, I mean supports porting to macOs and windows.

---

### Post by TheFu on 2017-06-30
Because nobody else has responded ... 

From the gtkmm.org website:
Cross-platform: Linux (gcc), FreeBSD (gcc), NetBSD (gcc), Solaris (gcc, Forte), Win32 (gcc, MSVC++ .Net 2003, 2005, 2008), MacOS X (gcc), others

Basically, you need to use gcc as the compiler, except on MS-Windows. There is an installer for Windows, but that might not be for the dev tools.  I've only touched OSX for about 2 weeks a few years ago. I wanted to like it.

I would always assume that grabbing the source and building the libraries would be my responsibility.  Any dependencies for the dev tools would also be my responsibility.

OTOH, I haven't developed with these libraries ... er ... ever.  So **I don't actually know anything**.

---

### Post by fallenshadow on 2017-07-04
Gtkmm is not really for designing cross platform apps. I have developed my main project PhotoFlare with both Gtkmm and Qt. Development is so much easier with Qt I can't even begin to describe how much better it is. The Gtkmm version has been abandoned for years since it was too hard to develop any decent new features with it and having an app completely cross platform is awesome.

If you want to build a cross platform app or even something decent for just Linux I would go with Qt5.

---

