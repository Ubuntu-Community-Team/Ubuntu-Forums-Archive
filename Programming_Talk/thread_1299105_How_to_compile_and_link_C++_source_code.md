---
title: "How to compile and link C++ source code"
date: 2009-10-23
forum: Programming Talk
---

### Post by abrrymnvette on 2009-10-23
At the risk of exposing how green I am to this. I'm trying to tech myself some C++ so I can at least read programs and understand them. 

My problem is, I've started with this tut [http://newdata.box.sk/bx/c/htm/ch01.htm](http://newdata.box.sk/bx/c/htm/ch01.htm)  and it assumes I know how to compile and link, which I don't. 

I open notepad, and wrote the things it says. Saved it as test.cpp. Now what? This is what I don't know what to do? I tried running it as ./test.cpp but got errors about unexpexted characters. Is that normal or was I supposed to compile and link it first? 

Thanks for the help! If I put this in the wrong forum/topic please move.

---

### Post by slavik on 2009-10-23
Moved to separate thread.

presuming you are on Linux.

open a terminal and navigate to where you cpp file is, then run the following command:

g++ -o test test.cpp

---

### Post by dwhitney67 on 2009-10-23
> **abrrymnvette said:**
> At the risk of exposing how green I am to this. I'm trying to tech myself some C++ so I can at least read programs and understand them. 

My problem is, I've started with this tut [http://newdata.box.sk/bx/c/htm/ch01.htm](http://newdata.box.sk/bx/c/htm/ch01.htm)  and it assumes I know how to compile and link, which I don't. 

I open notepad, and wrote the things it says. Saved it as test.cpp. Now what? This is what I don't know what to do? I tried running it as ./test.cpp but got errors about unexpexted characters. Is that normal or was I supposed to compile and link it first? 

Thanks for the help! If I put this in the wrong forum/topic please move.

Skip reading that tutorial, because it appears that it was written long ago.

If you want to develop a simple C++ program (similar to the tutorial), compile it, and then run it, follow these steps:

1.  Using your favorite editor, edit a file call hello.cpp with the following contents:
```

#include <iostream>   // note, in your tutorial, this was iostream.h;
                      // that's why I know it is an old tutorial

int main()
{
   using namespace std;  // This is the namespace where cout, endl,
                         // and a lot other Standard Template Library
                         // objects and containers reside.

   cout << "Hello world." << endl;

   return 0;  // this is optional, but some die-hard programmers like it.
}

```

To compile (and link):
```

g++ hello.cpp -o hello

```
To run the program:
```

./hello

```

---

