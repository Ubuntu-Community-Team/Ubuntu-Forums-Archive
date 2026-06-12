---
title: "Cross-Compile GTK"
date: 2012-09-12
forum: Packaging and Compiling Programs
---

### Post by ryn.cor21 on 2012-09-12
I have written a totally amazing GTK program that runs beautifully on Ubuntu 12.04 LTS. All I had to do was install "build-essentials" package and "gcc". Then I could place the code file named "code.c" in my home folder and run:
 
gcc code.c `pkg-config --cflags --libs gtk+-2.0`
 
... and the program would produce a binary named "a.out" which runs on Ubuntu just fine. (provided the card pictures are placed in "/Cards")
 
My question is: How do you get a GTK program to run on Windows?
I would like to show my programming teacher but he only has Windows machines at school.
 
I have a dual boot Windows-Ubuntu machine and Microsoft Visual Studio 2010 Ultimate. I have attempted to cross compile and even compile on windows, but I must tell you that I have no idea what im doing. Personally, I would be happier if every person ran Ubuntu.
 
This is my program:
```
 took code down[FONT=Consolas][SIZE=2]
[/SIZE][/FONT]
```
 
Any help is appreciated.

---

### Post by opensshd on 2012-09-12
You'll need a Win32 or WinMain function as entry point, windows.h. Read through this page and halfway down it has a section on adapting Linux source code to windows.

[http://www.ibiblio.org/apollo/WinGtkHowto.html](http://www.ibiblio.org/apollo/WinGtkHowto.html)

Might want to try MinGW instead of visual studio.

[http://mingw-w64.sourceforge.net/](http://mingw-w64.sourceforge.net/) 

More stuff I found: [http://zetcode.com/gui/winapi/window/](http://zetcode.com/gui/winapi/window/)

---

### Post by ryn.cor21 on 2012-09-12
I would like to thank you so very much because my program is now working! I felt like I had searched forever for a solution which makes me feel dumb because you linked me to one in five minutes.

---

### Post by opensshd on 2012-09-12
Please mark [Solved] in thread tools menu :) Glad it worked out!

---

