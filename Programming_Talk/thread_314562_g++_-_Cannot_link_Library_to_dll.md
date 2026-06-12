---
title: "g++ - Cannot link Library to dll"
date: 2006-12-07
forum: Programming Talk
---

### Post by Crypto-138 on 2006-12-07
Hello there. I'm trying to compile an extension for a program([Furnarchy2](http://www.heroinpuppy.com/forums/YaBB.cgi?board=furn2)) that adds features to an Online game, [Furcadia](http://www.furcadia.com/) for Windoze.

The thing of it is, I've never really used C++ extensively, or used the gcc compiler without an IDE. (Dev-C++).

I've been able to compile these "modules" on Windows, but for some reason, I'm having a hard time linking one of the libraries "furn2.lib" to the dll.

Luckily, the code for the module is OpenSource, so I uploaded it to my filecabin account in a tar.gz to see if anyone could help me.

I've been trying to compile it with the following commands as was suggested by the Furnarchy2's maker:

The .lib file HAS to be linked for it to work, but g++ can't seem to handle it. It's an AR archive according to Nautilus.

Link to Source: [Click Here.](http://www.filecabin.com/members_vb/files/97520/dummy.tar.gz)

---

### Post by thumper on 2006-12-07
It is not clear here whether or not you are doing development in windows or linux?

You cannot link a windows library (.lib) with code that you have compiled on linux using g++.  On linux dynamic link libraries (DLLs) are normally referred to as shared object libraries (.so).  The internal format of these are quite different, and you'll not be able (AFAIK) to create DLLs using g++ on linux.

---

### Post by po0f on 2006-12-07
Aren't *.lib files Windows static libraries?  If that's the case then:
```
[FONT="Courier New"]          static    dynamic
Windows   file.lib  file.dll
Linux     file.a    file.so[/FONT]
```
AFAIK there is no way to use a Windows-compiled library with Linux source.

---

### Post by Crypto-138 on 2006-12-08
> **po0f said:**
> Aren't *.lib files Windows static libraries?  If that's the case then:
```
[FONT="Courier New"]          static    dynamic
Windows   file.lib  file.dll
Linux     file.a    file.so[/FONT]
```
AFAIK there is no way to use a Windows-compiled library with Linux source.

Nonono. It's Windows Source. 
> **thumper said:**
> It is not clear here whether or not you are doing development in windows or linux?

All of this is for Windows, and run in WINE.

I guess I didn't really word my intentions well. ](*,)  
I'm trying to compile a DLL for a Windows game, but it freezes when I link that .lib file to the DLL through Mingw32.

Could it have to do with running all this on a x86_64 processor?

---

### Post by Crypto-138 on 2006-12-09
Hello?

---

