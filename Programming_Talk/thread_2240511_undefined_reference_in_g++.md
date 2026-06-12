---
title: "undefined reference in g++"
date: 2014-08-20
forum: Programming Talk
---

### Post by Anh_Tran on 2014-08-20
Hello guys,

I'm quite like a newbie in C++ and Ubuntu, so forgive me if I make some stupid mistakes. I tried compiling these files on Windows (Visual Studio '13) with no problem, file run just fined. Exactly what I'm looking for.

I switch to Ubuntu 14.04.1, then there is a problem.

filename: main.cpp
```

#include <iostream>
#include "add.h" // this brings in the declaration for add()
 
int main()
{
    using namespace std;
    cout << "\nHello, World!\n\nThe sum of 3 and 4 is " << add(3,4) << "\n" << endl;
    return 0;
}

```

filename: add.h
```

#ifndef ADD_H
#define ADD_H
 
int add(int x, int y); // function prototype for add.h
 
#endif

```

I try using these

g++ -Wall -W -Werror main.cpp -I. -o CPPHelloWorld

or just simply
g++ main.cpp -I. -o CPPHelloWorld

error message:
```
tmp/cccwZdcy.o: In function `main':
main.cpp:(.text+0x1a): undefined reference to `add(int, int)'
collect2: error: ld returned 1 exit status


```

Am I missing anything?

Thanks.

---

### Post by steeldriver on 2014-08-20
Hello and welcome to the forums

Where is the 'add' function actually defined?* Declaring *something is not the same as defining it - in this case, g++ is able to compile your file (because you have declared the function prototype for 'add') but the linker is failing to link the pieces together into an executable binary file

---

### Post by Anh_Tran on 2014-08-20
Ah, you are right, I'm missing one file add.cpp

```

// #include <iostream>

int add(int x,int y)
{
    return x+y;
}

```

It's still saying undefined reference to 'add(int, int)'

---

### Post by Anh_Tran on 2014-08-20
Problem solved. I forget to include add.cpp while executing g++ command in terminals.

Thanks for the hint, steeldriver!

---

