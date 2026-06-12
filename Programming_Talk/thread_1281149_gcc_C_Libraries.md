---
title: "gcc C Libraries?"
date: 2009-10-03
forum: Programming Talk
---

### Post by hsnm on 2009-10-03
I'm new about gcc's internal structure. I'm trying to find the C functions like printf, puts, scanf and many other libraries like this. I need to do some modifications to some of them but I don't know where they are kept? Are they part of gcc's source code or they're put into a difference place? 

Please help me with that!
Thank you

---

### Post by Vichfret on 2009-10-03
/usr/include

---

### Post by hessiess on 2009-10-03
> 
I need to do some modifications to some

Why would you want to modify standard library functions?

---

### Post by MadCow108 on 2009-10-03
the system calls are in glibc
[http://sourceware.org/glibc/](http://sourceware.org/glibc/)

you cal also get the sources with apt-get source glibc-source when you have source repositories enabled

---

### Post by phrostbyte on 2009-10-03
Be careful, if you break your libc you can break pretty much your system. :)

---

### Post by hsnm on 2009-10-03
In fact I'm aware of danger of playing with these libraries. But my project requires some testing over these but very minor. 

/usr/include only has the header files not the source files. 

Well I know glib is gnu's C library but I don't know where these files are kept on the system!!

---

### Post by jpkotta on 2009-10-03
There are no sources, normally.  There is a static archive /usr/lib/libc.a and a DLL /lib/libc.so.6.  The static archive is basically a zip file (actually an 'ar' file) of object files (.o), and the DLL is a massaged static archive.  This is how pretty much any library works in (Debian/Ubuntu) Linux.  Unless you're modifying the library you don't need the source, so the source is not distributed in the -dev packages.  You need to *apt-get source libc6* and probably also *apt-get build-dep libc6*.

---

### Post by hsnm on 2009-10-03
Great, thanks for the info. Then how can I replace the library with the modified one?

---

### Post by phrostbyte on 2009-10-03
Do your modifications inline and then rebuild the .deb using dpkg-buildpackage

then install the deb using dpkg -i thelibc.deb

Don't do this on your production system because it can fail. :)

---

### Post by phrostbyte on 2009-10-03
You might need some package if you don't have dpkg-buildpackage, maybe "ubuntu-devel" ?

---

### Post by nvteighen on 2009-10-04
I'd recommend you to do something in the lines of this:

1) Build your standard library into **/usr/local/lib** with a different name than whatever your glibc version has (e.g. libmystdc.so wouldn't be bad).
2) Call **ldconfig** as root to update the library cache.
3) When compiling, use the **-nostdlib** flag and link against your own Standard Library.

This is much safer than anything else for sure. But, be aware than some routines from the GNU C Standard Library will be used nevertheless (memset, memcpy & friends... look at gcc's manual)... To bypass that you should use another flag, but can render your application useless. Moreover, doing these things in a C++ program can fail miserably.

---

### Post by hsnm on 2009-10-06
I installed dpkg and got the source. I'm gonna try this out and see if I can get it right.

Thanks for the help. I couldn't find my answer while Googling!

---

### Post by hsnm on 2009-10-06
> **nvteighen said:**
> I'd recommend you to do something in the lines of this:

1) Build your standard library into **/usr/local/lib** with a different name than whatever your glibc version has (e.g. libmystdc.so wouldn't be bad).
2) Call **ldconfig** as root to update the library cache.
3) When compiling, use the **-nostdlib** flag and link against your own Standard Library.

This is much safer than anything else for sure. But, be aware than some routines from the GNU C Standard Library will be used nevertheless (memset, memcpy & friends... look at gcc's manual)... To bypass that you should use another flag, but can render your application useless. Moreover, doing these things in a C++ program can fail miserably.
I like this idea. Actually, I implemented some functions of my own. I just need to put them in a separate library and use them. I'll try this too.

---

