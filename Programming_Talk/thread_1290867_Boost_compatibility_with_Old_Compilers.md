---
title: "Boost compatibility with Old Compilers"
date: 2009-10-14
forum: Programming Talk
---

### Post by chingupt on 2009-10-14
HI,
We are planning to use Boost version 1.39 on Windows. In docs i found the
following:
----------------------------------------------------------------------------------------------------
Compilers Tested
Boost's primary test compilers are: 
o Linux: 
o GCC 4.3.3 on Ubuntu Linux. 
o Windows: 
o Visual C++ 7.1 SP1, 8.0 SP1 and 9.0 SP1 on Windows
XP. 
Boost's additional test compilers include: 
o Linux: 
o Intel 9.0 on Red Hat Enterprise Linux. 
o Intel 10.0 on Red Hat Enterprise Linux. 
o Intel 10.1 on 64-bit Linux Redhat 5.1 Server. 
o Intel 10.1 on Suse Linux on 64 bit Itanium. 
o Intel 11.0 on Red Hat Enterprise Linux. 
o Intel 11.1 on Red Hat Enterprise Linux. 
o GCC 3.4.3, GCC 4.0.1, GCC 4.2.4, GCC 4.3.3 and GCC
4.4.0 on Red Hat Enterprise Linux. 
o GCC 4.3.3 and GCC 4.4.0 with C++0x extensions on
Red Hat Enterprise Linux. 
o GCC 4.1.1, 4.2.1 on 64-bit Red Hat Enterprise
Linux. 
o GCC 4.1.2 on Suse Linux on 64 bit Itanium. 
o GCC 4.1.2 on 64-bit Redhat Server 5.1. 
o GCC Open64 4.2.2 on Red Hat Enterprise Linux. 
o GCC 4.3.4 on Debian unstable. 
o QLogic PathScale(TM) Compiler Suite: Version 3.1 on
Red Hat Enterprise Linux. 
o GCC version 4.2.0 (PathScale 3.2 driver) on 64-bit
Red Hat Enterprise Linux. 
o Sun 5.9 on Red Hat Enterprise Linux. 
o Windows: 
o Visual C++ 7.1 on XP. 
o Visual C++ 9.0 on XP. 
o Visual C++ 9.0 on Vista. 
o Visual C++ 9.0 on Vista 64-bit. 
o Visual C++ 9.0, using STLport 5.2, on XP and
Windows Mobile 5.0. 
o Visual C++ 10.0 beta. 
o Borland 5.9.3, 6.1.0, 6.1.3. 
o Borland C++ Builder 2007 and 2009. 
o Intel C++ 11.1, with a Visual C++ 9.0 backend, on
Vista 32-bit. 
o Intel C++ 11.1, with a Visual C++ 9.0 backend, on
Vista 64-bit. 
o GCC 4.3.3 and 4.4.0, on Mingw with C++0x features. 
o Solaris: 
o Sun C++ 5.7, 5.8, 5.9 on Solaris 5.10. 
o GCC 3.4.6 on Solaris 5.10. 
----------------------------------------------------------------------------------------------------
My concern is:
We are supposed to use Boost both for Linux and Solaris, but the compilers being used are slightly old.
On Debian Linux we have GCC 3.3 and on Solaris we have Sun WorkShop 6 update
2 C++ 5.3.
Is Boost compatible with these versions? Does this list mean that Boost is not compatible with older versions of Compiler?

---

### Post by wmcbrine on 2009-10-14
No, it doesn't mean that. It's a list of compilers they tested on, like it says -- not an exclusive list of all compilers it works on. Try it and see.

---

