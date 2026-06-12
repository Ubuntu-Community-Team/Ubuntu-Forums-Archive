---
title: "using getch() in gcc"
date: 2006-11-15
forum: Programming Talk
---

### Post by FuzZy2006 on 2006-11-15
Can you suggest me something similar to the getch() function in c++ that I can use in gcc?

---

### Post by sweemeng on 2006-11-15
there is something similar under the ncurse library. go check it out.

---

### Post by FuzZy2006 on 2006-11-15
i did sudo aptitude install ncurses. in a ncurses tutorials it says that I should use *gcc -lncurses program.cpp* to run the program. when i put #include<ncurses.h> in the program, it still says that it doesn't find ncurses. ](*,)

---

### Post by engineer on 2006-11-15
you need the ncurses-dev package.
it contains the header files, you need

---

### Post by Horsman on 2006-11-16
I'm pretty sure you just want something like:

#include <iostream>
main(){
 char c;        // new char c
 std::cin >> c; // read one char from the standard input stream
 std::cout << c << std::endl; // write char c to standard output stream
}

---

