---
title: "Qt4 and encoding"
date: 2009-01-01
forum: Programming Talk
---

### Post by Lo_c on 2009-01-01
Hi,

I'm having quite strange problems with qt4 and QString.
If I try to use qPrintable on a QString in order to print it, it displays a string without any special caracters (like é, à, É for example). It's surprising as I would have thought that on ubuntu, default encoding was utf8, but if instead of qPrintable (which is equivalent to toLocal8Bit().constData()) I use toUtf8().constData(), it works fine.

So I tried to know what was default local and all I get is "System" (using QTextCodec::codecForLocale()->name() ), whereas if I set the Local to Utf8, qPrintable works fine…

So my question is : what is "System" and where could I set it to be Utf-8 (except in the program because it works fine under Mac OS and Windows, so I would rather not write something in it if it is my configuration that is problematic).

I'm running intrepid, I tested it on two different laptops (both under Intrepid), with Eclipse and KDevelop and I'm quite running out of ideas…

Thanks for your help.

---

