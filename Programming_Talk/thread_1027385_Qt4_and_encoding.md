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

### Post by tseliot on 2009-01-01
Ubuntu uses utf-8 and [here]("http://doc.trolltech.com/4.3/qstring.html") (see the end of "Initializing a String") the documentation says that the qPrintable() macro "is equivalent to calling <QString>.toAscii().constData()".

[Here]("http://doc.trolltech.com/4.3/qtglobal.html#qPrintable") it says that is equivalent to str.toLocal8Bit().constData().

As regards "System":
> QTextCodec * QTextCodec::codecForLocale ()   [static]

Returns a pointer to the codec most suitable for this locale.

On Windows, the codec will be based on a system locale. On Unix systems, starting with Qt 4.2, the codec will be using the iconv library. Note that in both cases the codec's name will be "**System**".

Can't you detect whether you're compiling the application on Mac OS or Windows and use something like the following?
```
void QTextCodec::setCodecForCStrings ( QTextCodec * codec )   [static]

Sets the codec used by QString to convert to and from const char * and QByteArrays. If the codec is 0 (the default), QString assumes Latin-1.
```

---

### Post by Lo_c on 2009-01-01
Yes, I could detect on which OS I'm compiling, but someone running Gentoo told me that it worked fine, that's why I was wondering why the locale on Ubuntu wasn't utf8… And as I tested it on two different laptops I'm really surprised because it seems it's not my own configuration.

---

