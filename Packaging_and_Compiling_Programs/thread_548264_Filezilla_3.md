---
title: "Filezilla 3"
date: 2007-09-11
forum: Packaging and Compiling Programs
---

### Post by il.Boni on 2007-09-11
Hi,
I'm quite new with linux and I'm starting to understand how compile a program from source code. 
I tried to compile Filezilla v.3 released few days ago. From the site you can download a precompiled version  that works on my ubuntu Festy and the source code. 

FileZilla depends on the following libraries :
wxWidgets 2.8.4 or greater. I downloaded and compiled it in /opt without problems
libidn with Synaptic
GnuTLS 1.5.4 or greater.  I downloaded the 2.0 vs and compiled it in /opt  without problems

So through the configure parameter   --with-wx-prefix I set the correct wxWidgets path and with the parameter  --with-libgnutls-prefix I set the path for the GnuTLS

I don't update the previous installed version for wxWidgets and GnuTLS library, because other program use them.

If I try to compile my filezilla source code I got this error 
'libgnutls-config --version' returned 2.0.0, but LIBGNUTLS (1.4.4) was found!

I tried to set environment variables but it doesn't works.
For compile I use this command 
 ./configure --prefix=/opt --with-wx-prefix=/opt/wxGTK-2.8.4 --with-libgnutls-prefix=/opt/gnutls-2.0.0

So my questions are :
How can I compile with the correct LIBGNUTLS library?
Why If I download the compiled version of the programs it works without updated library? Is it because are static library, something like embedded in the compiled code?

thank you for your help ( and sorry for my english )
by
il.Boni

---

