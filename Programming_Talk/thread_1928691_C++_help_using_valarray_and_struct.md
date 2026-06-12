---
title: "C++ help using valarray and struct"
date: 2012-02-20
forum: Programming Talk
---

### Post by jsmidt on 2012-02-20
Hey everyone.  I am new to C++ and would like to create a struct containing a name and a valarray with 10 elements of double with a separate function that initializes those elements to 5.0.  (The program will get more complex but I can't even get this simple case working. :) )

This is my header file mystruct.h

```

#include <valarray>
#include <string>

struct myvec {
    std::string name;
    std::valarray<double> vec (10);
};

int init(myvec&);

```

and this is my .cpp file:

```

#include "mystruct.h"

int init(myvec& test)
{
    test.name = "testname";
    for (int i=0; i < 10; i++){
        test.vec[i] = 5.0;
    }

    return 0;
}

```

When I run:
```
g++ -c mystruct.cpp
```

I get the following error:

```
mystruct.h:6: error: expected identifier before numeric constant
mystruct.h:6: error: expected ',' or '...' before numeric constant
mystruct.cpp: In function 'int init(myvec&)':
mystruct.cpp:7: error: invalid types '<unresolved overloaded function type>[int]' for array subscript
```

Anyways, can anyone see my error.  I'm sure it is obvious but I am new.  Just want a struct containing a valarray with 10 elements, a name, and a separate function to initialize both the name and the elements of the valarray that I can make more complicated in the future.

Thanks!

---

### Post by muteXe on 2012-02-20
Hiya. Is this your whole code? Where's your main()?

---

### Post by jsmidt on 2012-02-20
main() exists and is just more complicated.  But I believe 
```
g++ -c mystruct.cpp
```

should compile independant of main() and is linked later so what is going on with main() is a separate issue.  Am I wrong?

---

### Post by Npl on 2012-02-20
lose the (10), if you want to initialize for 10 elements you need to write an constructor
```

#include <valarray>
#include <string>

struct myvec {
    std::string name;
    std::valarray<double> vec;
};
```

also you could try using a size_t instead of an int in your loop. Not sure, never used valarrays, and I hope you know you shouldnt use them unless you do operations on all (many) elements. Cause thats the only time they will be faster than normal arrays or lists

---

### Post by jsmidt on 2012-02-20
Npl, thanks, those were the two issues!  It compiles now.

---

