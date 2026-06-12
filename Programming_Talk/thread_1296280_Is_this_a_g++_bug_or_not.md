---
title: "Is this a g++ bug or not?"
date: 2009-10-20
forum: Programming Talk
---

### Post by Zugzwang on 2009-10-20
I must say that I don't see any mistake in the following program:
[PHP]
#include <iostream>
// #include <boost/utility.hpp>


class A /* : public boost::noncopyable */ {
private:
    A& operator=(const A& b) {
        std::cout << "Assignment operator" << std::endl;
        return *this;
    }

public:
    A() {
        std::cout << "Constructor" << std::endl;
    }

    A(const A &b) {
        std::cout << "Copy constructor" << std::endl;
    }
};

int main()
{
    A a(A());
    return 0;
}
[/PHP]

```

user@user-laptop:/tmp$ g++ -pedantic -Wall test.cpp
user@user-laptop:/tmp$ ./a.out
user@user-laptop:/tmp$ g++ --version
g++ (Ubuntu 4.3.3-5ubuntu4) 4.3.3
Copyright (C) 2008 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

```

It compiles fine. When running, exactly nothing happens. This is surprising, as at least the constructor and the destructor should be called. Having the class A deriving from boost::noncopyable doesn't change anything, so the compiler shouldn't call any automatically synthesized function. Also, changing the line "A a(A());" to "A a(A);" does not change anything.

Indeed, when looking at the generated assembler code, nothing is called.

It might be the case that the compiler thinks that "A a(A())" is a function declaration. However, the line "A a = A(A());" makes only one constructor being called and not the copy constructor, which is again problematic.

---

### Post by dwhitney67 on 2009-10-20
Yeah, weird behavior.  I'm sure there's an explanation for it somewhere in the bowels of the GCC spec.

Strangely enough, if you change the line of code in your main() function to be the following, the app works as "expected"... well, at least the basic no-arg constructor is called.  I'm not sure what happened to the copy-constructor.
```

...
A a( (A()) );
...

```

EDIT:  I bet GCC is treating your declaration as a function declaration, not an object declaration.  Only when the extra parenthesis are added, are things made clearer to GCC as to the intent of the statement.

---

### Post by johnl on 2009-10-20
I added a function x() to a, and added 'return a.x()' to main.  I got the following error which seems to confirm that g++ thinks this is a function declaration.

```

g++     test.cc   -o test
test.cc: In function 'int main(int, char**)':
test.cc:30: error: request for member 'x' in 'a', which is of non-class type 'A ()(A (*)())'

```

Whether or not this is a bug or expected behavior, I can't tell you.

---

### Post by MadCow108 on 2009-10-20
my guess is that is has to do with the fact that A() is a temporarie which is never bound to anything and thus just disappears (strange that there is no warning/error)

dwhitney's change shows this:
A a( (A()) );
here a temporarie A is created, not bound to const reference in its braces => it disappears, leaving this:
A a;
which calls the normal constructor

---

### Post by Zugzwang on 2009-10-21
So I finally found the "solution" to the problem that the copy constructor is never called. Apparently, the C++ standard allows skipping the construction of the temporary object altogether (as MadCow108 guessed) even in cases in which the constructor and the destructor of the class have side-effects.

See here: [http://gcc.gnu.org/onlinedocs/gcc-4.4.2/gcc/C_002b_002b-Dialect-Options.html](http://gcc.gnu.org/onlinedocs/gcc-4.4.2/gcc/C_002b_002b-Dialect-Options.html), section "-fno-elide-constructors"

---

### Post by CptPicard on 2009-10-22
[http://www.yosefk.com/c++fqa/ctors.html#fqa-10.19](http://www.yosefk.com/c++fqa/ctors.html#fqa-10.19)

(Kudos to Can+~ for tracking this down)

---

