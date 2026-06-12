---
title: "cout not working in gcc"
date: 2010-10-19
forum: Programming Talk
---

### Post by c2tarun on 2010-10-19
hi friends
i tried to compile the following c++ program with gcc compiler.

```
#include<iostream>

int main()
{
    cout << "hi this is my first program\n" ;
    return 0;
}

```


i saved it with filename try.C
then on terminal

```

$ gcc try.C

```

i also tried to save it with filename try.cpp
but in both the cases i m getting the following error.

try.C: In function ‘int main()’:
try.C:5: error: ‘cout’ was not declared in this scope


please explain why is this happening.

---

### Post by amauk on 2010-10-19
```
#include<iostream>

int main()
{
    [COLOR="Red"]std::[/COLOR]cout << "hi this is my first program\n" ;
    return 0;
}
```

also,
use g++, rather than gcc

---

### Post by c2tarun on 2010-10-19
> **amauk said:**
> ```
#include<iostream>

int main()
{
    [COLOR=Red]std::[/COLOR]cout << "hi this is my first program\n" ;
    return 0;
}
```also,
use g++, rather than gcc



hey it worked. thanx
can you please explain a bit.

---

### Post by sisco311 on 2010-10-19
[http://en.wikipedia.org/wiki/Namespace_(computer_science)#C.2B.2B](http://en.wikipedia.org/wiki/Namespace_(computer_science)#C.2B.2B)

---

### Post by dwhitney67 on 2010-10-19
The "std" is the name of the namespace where C++ libraries and components reside.

The use of "g++" is to compile/link with the C++ library.  It is equivalent to using "gcc" when linking with the "-lstdc++" library.

So, you have two choices:
```

g++ try.C

# or

gcc try.C -lstdc++

```
In this busy world where we have very little time to waste, which statement above do you think will take less time to type?

---

### Post by amauk on 2010-10-19
GCC is the GNU C compiler
G++ is the GNU C++ compiler

Technically, GCC & G++ are the same
(G++ just invokes GCC with some predefined options for compiling C++)

The C++ standard libraries are contained within the namespace "std" (short for standard)
If you wish to use objects from the standard library, you need to include it's namespace when calling them

std::cout << "something"
=
Send the string "something" to the "cout" object in the namespace "std"
=
Output "something" to the standard output stream

Namespaces help prevent name clashes, by organising objects into discrete sets, and eliminating the need to every object/function to have a unique name
It's the namespace::object that's now unique

---

