---
title: "Method declaration in C++"
date: 2008-11-22
forum: Programming Talk
---

### Post by jimi_hendrix on 2008-11-22
i know theres two ways to declare methods of classes in C++...the

```

class foo
{
     void bar()
     {
      }
};
```

and

```

class foo
{
     void bar();
};

foo::bar()
{
}

```

i prefer the first way but i almost always see the second way...is there some advantage to the second way or is that just more popular?

---

### Post by SledgeHammer_999 on 2008-11-22
The second one is easier to read. Imagine a class with ten methods. And then imagine that each method has 20 lines of code. It is going to be really hard to understand and read it.

Also if you just declare the class prototype(your 2nd example) you can use your class in any code before you actually define each and every method, because the compiler already knows of what methods your class is made of.

EDIT: it's actually
[php]
class foo
{
     void bar();
};

void foo::bar()
{
}
[/php]

---

### Post by jimi_hendrix on 2008-11-22
ill make a new post for this...forget it

---

### Post by nvteighen on 2008-11-22
I don't know C++, so let me ask. If you were to write a C++ header file, can you just use:

```

class MyClass
{
public:
    void foo();
private:
    void bar();
};

```

---

### Post by jimi_hendrix on 2008-11-22
i believe...ive only made my own header once and it was for C

---

### Post by nvteighen on 2008-11-22
What I mean is if the C knowledge of prototypes is also valid in C++...

---

### Post by snova on 2008-11-22
It is.

Oh, and jimi_hendrix, the point is that with the latter, you can split the code into another file.

---

### Post by WW on 2008-11-22
> **jimi_hendrix said:**
> i know theres two ways to declare methods of classes in C++...the

```

class foo
{
     void bar()
     {
      }
};
```

and

```

class foo
{
     void bar();
};

foo::bar()
{
}

```

i prefer the first way but i almost always see the second way...is there some advantage to the second way or is that just more popular?

The first method combines both the declarations and the definitions of the class methods.  This is fine if you are putting all your code in one file (e.g. everything that you are writing is in main.cpp).  The second method is preferable if, say, you have multiple source files, several of which use the class.  You might want to treat the class as a library to be used within your application.  Then you would have something like:

mylib.h
```

class foo
{
     void bar();
};

```

mylib.cpp
```

#include "mylib.h"

foo::bar()
{
}

```

myapp.cpp
```

#include "mylib.h"

int main()
    {
    foo f;
    f.bar();
    // etc.
    }

```

myutilities.cpp
```

#include "mylib.h"

// more code that uses the class...

```
Each .cpp file can be compiled separately, and then all the .o files can be linked.

---

