---
title: "Compiling for windows in linux?"
date: 2009-02-10
forum: Programming Talk
---

### Post by StOoZ on 2009-02-10
Is it possible to compile a C++ code in linux and then run it on windows?? (to create statically linked executables?)

my code consists of only C++ STL and standard functions with the use of libCurl and boost regex.

thanks,

---

### Post by johnl on 2009-02-10
If you install the mingw32 packages you can use it to compile a windows executable.  Instead of using 'g++' simply use 'i586-mingw32msvc-g++'.

You will need to get the windows versions of the libraries you are using, however.

---

### Post by StOoZ on 2009-02-10
I see , thanks.

but how do I install the windows libs of linux???

---

### Post by OuahabiX on 2009-02-10
Let an old Win32 coder advice you.

You can either use the MingW compiler or you can download the Win version of the MingW Developer Studio and run it through Wine, it will work perfectly and it will produce a 100% native Windows Applications from both C and C++ simple or complicated source codes, and you don't need to use the terminal to set the Parameters, the IDE does, and you don't need to download any further libs, they've already been  included with it.

Download the Full version 125MB with all the Win32 API Libs from:
[http://www.iit.upcomillas.es/libroc/MinGWStudioFullSetupPlus-2_05.exe](http://www.iit.upcomillas.es/libroc/MinGWStudioFullSetupPlus-2_05.exe)

Or the small one without the full Libs 25MB only:
[http://www.iit.upcomillas.es/libroc/MinGWStudioFullSetup-2_05.exe](http://www.iit.upcomillas.es/libroc/MinGWStudioFullSetup-2_05.exe)

This works great for me and I hope it will do so for you too.

---

### Post by WW on 2009-02-11
Search the forum for "cross compiling" to find additional threads about this topic.

I haven't tried Ouahabix's second suggestion (MingW Developer Studio with Wine), but it sounds ideal if it works.  You'll still need to get the windows versions of the libcurl and boost libraries (if you download precompiled binaries) or cross compile them (if you build them from source) to create your statically linked executable.

---

