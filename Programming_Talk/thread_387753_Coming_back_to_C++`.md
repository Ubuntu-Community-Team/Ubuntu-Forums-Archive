---
title: "Coming back to C++`"
date: 2007-03-18
forum: Programming Talk
---

### Post by Timtro on 2007-03-18
Hello all,

This is an embarrassing question for me to ask. I haven't used C++ in a long time. I fell to C, then all the way to Fortran (clearly for scientific work). Now I want to go back and pick up some C++ again, and perhaps start writing some nice GUI stuff :)

Anyhow, I figured the best place to start is a nice "Hello World" program. I sat and squinted and scratched my head, and belted out a few lines from my memory:

```

#include <iostream>

int main()
{
    cout << "Hello World!"<< endl;
    return 0;
}

```

I brought up my terminal and g++'d my code and!! it didn't work. 

I did some googling and found that I needed to add 
```
using namespace std;
``` 
to my preamble (the bit before main() ).  Why? What on earth has happened? Are my old C++ books 1994 obsolete?

Thanks.

---

### Post by Sanchopinky on 2007-03-18
Supposedly it's so the program can recognize the built in functions you are using, but I could be wrong.

---

### Post by lnostdal on 2007-03-18
> **Timtro said:**
> Are my old C++ books 1994 obsolete?
yes, STL-stuff has been pushed inside the "std" namespace .. there are free books out there, "Thinking in C++" for instance

---

### Post by thumper on 2007-03-18
> Are my old C++ books 1994 obsolete?
Yes, and so are most books pre-1998.  C++ was accepted as an ISO standard around this time, and everything prior to that is most likely wrong, out dated or both.

---

