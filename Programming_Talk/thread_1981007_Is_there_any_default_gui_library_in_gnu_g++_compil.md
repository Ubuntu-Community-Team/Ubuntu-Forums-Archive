---
title: "Is there any default gui library in gnu g++ compiler?"
date: 2012-05-16
forum: Programming Talk
---

### Post by abhishektrivedi on 2012-05-16
Is there any default gui library comes bundled with gnu g++ compiler or i has to use qt or gtk for gui programming in linux?

---

### Post by codemaniac on 2012-05-16
I would vote for Qt .It is multi platform ,so if you want to port your application to Windows, Mac or some Mobile devices you can do it with minimal effort.

---

### Post by nothingspecial on 2012-05-16
*Thread moved to **Programming Talk**.*

---

### Post by xytron on 2012-05-16
I like[ FLTK]("http://www.fltk.org/").  It's always a good idea to consider portability.  Being tied to a single platform limits your application's potential use.

FLTK is very easy to use in Linux and with Visual Studio 2010.

---

### Post by Zugzwang on 2012-05-17
It is time that someone answers to the actual main question of the OP.

No, there is no default GUI library in the GNU g++ compiler and/or Linux. On Windows, you have built-in functions for window making, etc, and every compiler comes along with the header files to access these. In Linux, the graphical user interface is provided by the X Server. Its functionality can be directly accessed by using the libX. Here, you still need a library for this since there is server/client communication involved. While you could program your GUI application in libX directly, only very few programs actually use it directly, because it only has rudimentary functionality for drawing and the like, so it is very cumbersome. Thus, one typically uses some widget library that builds upon libX that provides all the lists and buttons you need. Examples for these libraries are indeed QT and GTK. More of them can be found at [http://en.wikipedia.org/wiki/Widget_library](http://en.wikipedia.org/wiki/Widget_library)

A quick note on xytron's post: his/her comment on portability suggests that at least some of the widget toolkits mentioned in this post are not cross-platform. This is however not the case: QT, GTK, and FLTK are all cross-platform.

---

### Post by xytron on 2012-05-17
> **Zugzwang said:**
> 
A quick note on xytron's post: his/her comment on portability suggests that at least some of the widget toolkits mentioned in this post are not cross-platform. This is however not the case: QT, GTK, and FLTK are all cross-platform.


I didn't mean to suggest that the other toolkits are not cross-platform.  However I tried to initially use GTK in Windows and found it very difficult to set up with Visual Studio 2010.  I'm sure people have accomplished it I found it rather complicated and error prone.

---

### Post by Bachstelze on 2012-05-17
This is not a problem of OS but of development environment. GTK is very UNIXy in nature, you don't use Visual Studio to compile it in Windows, you use some UNIX-like environment such as Cygwin or MinGW.

---

