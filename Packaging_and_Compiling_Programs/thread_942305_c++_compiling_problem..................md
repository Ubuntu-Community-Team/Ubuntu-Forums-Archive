---
title: "c++ compiling problem................."
date: 2008-10-09
forum: Packaging and Compiling Programs
---

### Post by abhilashm86 on 2008-10-09
i am not able to execute c++ program.........
abhilash@abhilash-desktop:/bin$ sudo g++ binary.cpp
binary.cpp: In function ‘int main()’:
binary.cpp:5: error: ‘cout’ was not declared in this scope
binary.cpp:5: error: ‘endl’ was not declared in this scope
binary.cpp:7: error: ‘cin’ was not declared in this scope

when i executed above prgm,compiler is not recognising cout,endl etc............i used
#include<iostream>
int main()
as libraries..............how to overcome this problem..............

---

### Post by sheto on 2008-10-20
Could I please see your code?

---

### Post by issih on 2008-10-20
I suspect  you need to add the line:

"using namespace std;"

after your imports. its required to access things in the standard libraries without prefaceing them with std::.

hope that helps

---

