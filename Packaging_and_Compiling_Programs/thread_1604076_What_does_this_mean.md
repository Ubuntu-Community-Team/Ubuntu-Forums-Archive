---
title: "What does this mean?"
date: 2010-10-23
forum: Packaging and Compiling Programs
---

### Post by layers on 2010-10-23
Hi. I hope this was the right place to put this.

I have a simple Makefile, and it is giving me things I have no idea what they mean.

```

ibo@ibo-laptop:~/Desktop$ ls
calibre.desktop  gnome-terminal.desktop  matlab        t
Driver.cpp       google-chrome.desktop   matlab7       t.cpp
Driver.h         main.cpp                scilab-5.2.2  test.cpp
Employee.cpp     main.o                  Staff.cpp     thunderbird.desktop
Employee.h       Makefile                Staff.h       t.o
ibo@ibo-laptop:~/Desktop$ make
g++ -c Driver.cpp -o Driver.o
Driver.cpp:4: fatal error: Driver.h: No such file or directory
compilation terminated.
make: *** [Driver.o] Error 1
ibo@ibo-laptop:~/Desktop$ 

```

I am interested in understanding what this line means:

Driver.cpp:4: fatal error: Driver.h: No such file or directory

---

### Post by layers on 2010-10-23
Just to answer my own question, and/or other people who come to the same one : your header files ("*.h") are included along with "", not <>.

---

