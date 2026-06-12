---
title: "c++ compiling"
date: 2010-02-02
forum: Programming Talk
---

### Post by vijesh758 on 2010-02-02
i got this message while try to compile please help me
vijesh@computer:~$ sudo gedit myprogram.cpp
vijesh@computer:~$ g++ myprogram.cpp -o myprog
myprogram.cpp:1:21: error: iostream.h: No such file or directory
myprogram.cpp:2:18: error: conio.h: No such file or directory
myprogram.cpp:3: error: ‘::main’ must return ‘int’
myprogram.cpp: In function ‘int main()’:
myprogram.cpp:6: error: ‘clrscr’ was not declared in this scope
myprogram.cpp:7: error: ‘cout’ was not declared in this scope
myprogram.cpp:8: error: ‘cin’ was not declared in this scope
myprogram.cpp:10: error: ‘getch’ was not declared in this scope

---

### Post by Chamillionaire2 on 2010-02-02
Try using gcc instead.

---

### Post by lisati on 2010-02-02
Isn't gcc for C programs and g++ for C++?

Try this instead:
```
sudo apt-get install build-essential
```

---

### Post by smdawson on 2010-02-02
Could you post the code, and explain what you did? I'm new to programming and could be wrong, but it looks like you possibly did not declare a namespace, or maybe initialize your variables.

---

### Post by smdawson on 2010-02-02
...actually, listen to the other two guys. :)

---

### Post by nvteighen on 2010-02-02
g++ is for C++; gcc is for C. Both are part of GCC, the GNU Compiler Collection. I hope that clears things up.

Now, current C++ doesn't use the .h extension for standard headers any longer. Standard headers like iostream, fstream, math, etc. are referred as that, while non-standard ones are required to have .h as extension.

Also, conio.h is a **C** header specific for **MS-DOS**. In the UNIX and Unix-like world, the features you get in conio.h are part of the ncurses library, but be aware that it's a C library too and though there are C++ bindings for it, I haven't found any in the Debian/Ubuntu repositories yet... maybe I haven't searched well :P

---

