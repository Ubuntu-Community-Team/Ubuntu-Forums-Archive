---
title: "c++ linux specific guidence needed"
date: 2010-09-27
forum: Programming Talk
---

### Post by akvino on 2010-09-27
What is the best way to check last modification time on the file and test if the file exists using C++ on Linux? I found C code that references unistd.h and st_mtime. Is that the best approach?

Sample of some sort would be appriciated if handy?

---

### Post by spjackson on 2010-09-28
Using purely the C and C++ libraries on Linux... For file modification time you need to call stat (man 2 stat). For testing whether a file exists there's access (man 2 access).

In C++ land... If you are using boost, then boost/filesystem has functions exists and last_write_time.  If you are using Qt, then QFileInfo has exists and lastModified. Both of these libraries are cross-platform.

---

### Post by PaulM1985 on 2010-09-28
I have used this quite alot for work in C/C++.  It is a C library which is pretty useful for file system information.  Maybe you could write a C++ wrapper if you wanted something object oriented.

[http://www.gnu.org/s/libc/manual/html_node/File-System-Interface.html#File-System-Interface](http://www.gnu.org/s/libc/manual/html_node/File-System-Interface.html#File-System-Interface)

Paul

---

