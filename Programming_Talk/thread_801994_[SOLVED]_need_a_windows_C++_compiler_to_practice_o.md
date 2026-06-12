---
title: "[SOLVED] need a windows C++ compiler to practice on my work machine"
date: 2008-05-21
forum: Programming Talk
---

### Post by go_lanche on 2008-05-21
I am working on learning C++ and have everything rocking at home with GCC. I have recently decided to spend some of my downtime at the office working on C++. Any suggestions on open source compilers for Windows 2000 would be greatly appreciated. I am not overly excited about running Cygwin and was hoping for other ideas. Thanks for the help with this particular issue and for all the awesome help for beginning programmers in general on these forums (this means you LaRoza!).

---

### Post by luisromangz on 2008-05-21
Try this:

[http://www.delorie.com/djgpp/](http://www.delorie.com/djgpp/)

---

### Post by AnRa on 2008-05-21
[MinGW]("http://www.mingw.org/")

---

### Post by jespdj on 2008-05-21
There's also [Microsoft Visual C++ Express Edition](http://www.microsoft.com/express/vc/), the free (as in no cost) version of Visual C++. (I'm not sure if it runs on Windows 2000, though...).

---

### Post by noerrorsfound on 2008-05-21
> **jespdj said:**
> There's also [Microsoft Visual C++ Express Edition](http://www.microsoft.com/express/vc/), the free (as in no cost) version of Visual C++. (I'm not sure if it runs on Windows 2000, though...).
That's an IDE, though.

---

### Post by LaRoza on 2008-05-21
> **go_lanche said:**
> I am working on learning C++ and have everything rocking at home with GCC. I have recently decided to spend some of my downtime at the office working on C++. Any suggestions on open source compilers for Windows 2000 would be greatly appreciated. I am not overly excited about running Cygwin and was hoping for other ideas. Thanks for the help with this particular issue and for all the awesome help for beginning programmers in general on these forums (this means you LaRoza!).

For Install: [http://www.bloodshed.net/devcpp.html](http://www.bloodshed.net/devcpp.html)

For Portable use (on flash drive or just not installed): [http://sourceforge.net/projects/devcpp-portable](http://sourceforge.net/projects/devcpp-portable)

Both use MinGW and can be used from the command line if the appropriate path variable is set. (Use just like gcc or g++ on Linux)

If you don't have access to a good editor you can go find a portable one (try portableapps.com, they have a good one) or just use the IDE. It is simple enough.

For the portable version, you can just unpack it (double click) and use on Windows. No need to be admin.

---

### Post by jespdj on 2008-05-21
> **noerrorsfound said:**
> That's an IDE, though.
But you get the Microsoft C++ compiler with it, ofcourse.

---

### Post by Martin Witte on 2008-05-21
> **jespdj said:**
> There's also [Microsoft Visual C++ Express Edition](http://www.microsoft.com/express/vc/), the free (as in no cost) version of Visual C++. (I'm not sure if it runs on Windows 2000, though...).
Have to withdraw my commet on running on 2000 - didn't read carefully....

---

### Post by curvedinfinity on 2008-05-21
I'll second MinGW/MSYS. Works great and is 100% compatible with Linux's GCC. Microsoft's compiler has a number of differences which makes porting code in between Linux and Windows difficult.

---

### Post by lavinog on 2008-05-21
you could also ssh to your box. this way you can work on the same project at and away from home.

---

