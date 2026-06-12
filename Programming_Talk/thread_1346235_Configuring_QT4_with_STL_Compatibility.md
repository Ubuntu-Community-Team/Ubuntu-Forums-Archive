---
title: "Configuring QT4 with STL Compatibility"
date: 2009-12-04
forum: Programming Talk
---

### Post by shynthriir on 2009-12-04
Attempting to use functions fromStdString and toStdString, but according to the QT4 docs:

"This constructor is only available if Qt is configured with STL compatibility enabled."

I've looked through the docs and searched a bit online, but can't find out HOW to enable STL compatibility.

---

### Post by haTem on 2009-12-05
I think it is done by passing the appropriate configure flag while compiling qt4. Based on some searching, it looks like you can either pass -stl or -no-stl to ./configure.

What operating system/packages are you using? I believe STL compatibility has been enabled on pretty much everything I've used qt4 on.

---

### Post by shynthriir on 2009-12-05
Ubuntu 9.10
g++ 4.4.1
QMake 2.01a
QT4 4.5.2

Tried doing just ./configure and just configure with the -stl tag along with each, but in first case, that implies I have an executable to run in my current directory, so if that's the case, where must I run that command. Second, if the ./ doesn't need to be there, then it should be a program or something, which it doesn't seem to be either.

---

### Post by haTem on 2009-12-05
Ubuntu 9.10 has STL compatibility enabled for qt4, it works on my system. What errors do you get when you try to use fromStdString and toStdString?

STL compatibility has to be enabled while compiling the qt4 library itself, not from your individual project's directory. So you would have to rebuild the packages supplied by Ubuntu to enable it. However, I'm using the exact same packages (on Ubuntu 9.10) and STL compatibility is enabled, so this is most likely not your problem.

---

