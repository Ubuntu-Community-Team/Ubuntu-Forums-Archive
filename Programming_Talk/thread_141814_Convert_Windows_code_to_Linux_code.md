---
title: "Convert Windows code to Linux code"
date: 2006-03-09
forum: Programming Talk
---

### Post by kombipom on 2006-03-09
Hi,

Sorry if this has been asked before but I couldn't find it.

If I get the source code for an app written on Windows using Dev-C++ would it be a nightmare to get it to compile and run in Ubuntu?  Are there any guides/tools for doing this sort of conversion.  The app is a driver for a chording keyboard that plugs into a COM port if that helps at all.

As you can no doubt tell I know naff all about programming beyond a bit of shell scripting and using perl to manipulate text files.

Thanks for looking.

---

### Post by HokeyFry on 2006-03-09
I am no expert, but if it is written in standard C++ then there shouldn't be a problem.

---

### Post by kbsucks on 2009-06-08
what if the code is using windows libraries and headers, classes

for eg: CString 

equallant thing in std cpp ?

---

### Post by Arppa on 2009-06-08
No device driver can be written entirely in standard c++. They always use platform specific APIs, thus they are operating-system-specific. If you want your windows driver working in linux you'd have to start writing the driver pretty much from scratch. This is quite a big project and if you haven't programmed c/c++ and drivers before I can't recommend trying it.

---

### Post by monkeyking on 2009-06-08
I dont think there is a easy painfree solution to your problem.

---

### Post by dwhitney67 on 2009-06-08
Besides me, has anyone bothered to look at the date of the OP... way back in 2006.

---

### Post by PmDematagoda on 2009-06-08
> **dwhitney67 said:**
> Besides me, has anyone bothered to look at the date of the OP... way back in 2006.

Which is why this thread is closed, if the new OP wants to ask the question again, he may do so from a new thread of his own.

---

