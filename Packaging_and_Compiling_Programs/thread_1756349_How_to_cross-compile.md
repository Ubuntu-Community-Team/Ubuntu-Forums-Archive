---
title: "How to cross-compile?"
date: 2011-05-12
forum: Packaging and Compiling Programs
---

### Post by kirkkaf on 2011-05-12
Hi everyone,

I am very new to Linux and am enjoying every moment of it. However I would still like to develop programs for Windows.

I have gone through this tutorial here: [http://www.linfo.org/create_c1.html]("http://www.linfo.org/create_c1.html")

Which took me through the steps of starting a program in C and compiling it with gcc. This compiles fine and runs okay.

However I want to compile the same program for Windows is this possible with gcc and how would I go about doing so?

Thank you for your time.

---

### Post by fpissarra on 2011-05-13
> **kirkkaf said:**
> Hi everyone,

I am very new to Linux and am enjoying every moment of it. However I would still like to develop programs for Windows.

I have gone through this tutorial here: [http://www.linfo.org/create_c1.html]("http://www.linfo.org/create_c1.html")

Which took me through the steps of starting a program in C and compiling it with gcc. This compiles fine and runs okay.

However I want to compile the same program for Windows is this possible with gcc and how would I go about doing so?

Thank you for your time.

I believe this is not the correct sub-forum for this question, but I have an answer for you: MinGW32

```
sudo apt-get install mingw32
```

Once installed you can use /usr/bin/i586-mingw32msvc-gcc to compile your C programs for Win32. The only thing is that you must distribute one DLL with your executable: mingwm10.dll (you can find this at /usr/share/doc/mingw32-runtime/mingwm10.dll.gz - maybe you'll have to install mingw32-runtime package).

Ahhhh... there is a mingw64 as well, but I have no experience with this one.

Regards...

---

### Post by kirkkaf on 2011-05-13
Thank you for your help just want I needed. \\:D/

Kirk.

---

### Post by cgroza on 2011-05-13
What are the drawbacks of using a cross compiler?

---

