---
title: "C++ book for ubuntu?"
date: 2013-09-16
forum: Programming Talk
---

### Post by josh17 on 2013-09-16
Are there any programming books for C++ that focus on the ubuntu platform? I have one but it is on windows so I assume things like #include <iostream> would be somewhat different on ubuntu. Any books or online resources would be appreciated :)

---

### Post by TheFu on 2013-09-17
I don't have any recommendation for books - they are out of date before being printed.  If you do want a book, just avoid any specific to Windows or OSX.

Standard C++ is standard C++ regardless of the platform.  If you stay with standard libraries, the code will work. This is harder for GUI programs, since more platform specifics is often desired - like MFC.  In the Linux/UNIX world, using cross-platform GUI libraries is really the best way - Qt, GTK, etc....  I think there are others.

#include <iostream>  works exactly the same regardless of platform.

You could program like we did in the old days with XLIB, xm, xt, but that would be too painful.

Programming specifically for Ubuntu would not really be recommended either, why prevent Fedora, Debian, Mint, CentOS, RHEL, and all the others from running your FANTASTIC program?

---

### Post by nathan-b on 2013-09-19
```
#include <iostream>
``` is part of standard C++, so it will be the same anywhere you have a c++ compiler. However, if you look at C++ code written for windows and it has types or macros like lpstr, wWinMain, LRESULT CALLBACK etc., that will not work in Ubuntu. Ubuntu will only be confused. :)

I'm not sure I agree with the advice above about not getting books. I just bought the 4th edition of "The C++ Programming Language" and expect that it will be useful for at least a decade or more. I will say that most libraries you would want to use have more or less complete documentation online, making a book superfluous. Qt's documentation is awesome, for example. I didn't think Gtk's was as thorough but it is still well documented. The cool thing is, and I just found out about this, is that Ubuntu provides html documentation for lots of libraries in the repositories. I installed the qt4-doc-html package and now I have everything I would want to know about Qt available in my browser even if the Internet is unavailable.

Look at [http://www.cplusplus.com/reference/](http://www.cplusplus.com/reference/) . Everything there, such as <vector>, <string>, etc. will work on Linux and Windows. There is also a C++ tutorial on that website I think.

---

