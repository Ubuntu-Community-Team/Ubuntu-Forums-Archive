---
title: "newbie trouble w/ c++"
date: 2011-05-30
forum: Programming Talk
---

### Post by eyeeeyeohyu on 2011-05-30
So, hey, i'm an Ubuntu newbie and new to programming in general, so i wanted to get a handle on c++ programming for an upcoming class that uses it by going through the C++ edition of "how to think like a computer scientist". only problem is, whenever i try to compile a program, the computer starts throwing errors. heres a sample of the code i  put in, verbatim from the book:

 #include <iostream.h>
// main: generate some simple output
void main ()
{
cout << "Hello, world." << endl;
return 0
}

and heres what i get out:

hello.cpp:3: error '::main' must return 'int'
hello.cpp: in function 'int main()':
hello.cpp:5: error: 'cout' was not declared in this scope
hello.cpp:5: error: 'endl' was not declared in this scope
Compilation failed.

i must've installed 3 or 4 different environments (i have geany installed right now) and i tried it in the terminal too. I even upgraded Ubuntu versions. Please please please, tell me what I'm doing wrong.

---

### Post by muteXe on 2011-05-30
Nothing to do with IDEs or versions of ubuntu.
Just address the errors your compiler's telling you about!

1. if you're returning a value then do "int main()", rather than void.
2. it does not recognise endl or cout because you have not told the compiler they belong to the std namespace. You need to write std::endl and std::cout, or declare this namespace underneath your include with the 'using' keyword.

Hope that helps chap.

---

### Post by dwhitney67 on 2011-05-30
@ the OP

Get yourself a new study book; the one you have is over a decade old.

Do not append the .h to the iostream header file; if your book is indicating to append the .h, then scratch it out with a pencil/pen.

As Mutexe indicated, cout and endl are part of the std namespace; thus to use these members, you have two choices: 1) use a "using namespace" directive in your code, or 2) fully qualify cout and endl with their namespace.  For example:
```

#include <iostream>
using namespace std;

...

cout << "hello world" << endl;

```
or
```

#include <iostream>

...

std::cout << "hello world" << std::endl;

```
Lastly, the main() function should ALWAYS be declared to return an int.  Defining it as a void function is incorrect.  In C++, returning a value at the end of the main() function is optional; if you do not specify a value, then by default, 0 (zero) is returned.

---

### Post by rpmp on 2011-05-30
it supposed to be like:

// my first program in C++

#include <iostream>
using namespace std;

int main ()
{
cout << "Hello World!";
return 0;
}

---

### Post by hakermania on 2011-05-31
If you followed a tutorial and came up with this as example, then it is outdated!
Use other tutorial!

---

### Post by Petrolea on 2011-05-31
> **eyeeeyeohyu said:**
> So, hey, i'm an Ubuntu newbie and new to programming in general, so i wanted to get a handle on c++ programming for an upcoming class that uses it by going through the C++ edition of "how to think like a computer scientist". only problem is, whenever i try to compile a program, the computer starts throwing errors. heres a sample of the code i  put in, verbatim from the book:

 #include <iostream.h>
// main: generate some simple output
void main ()
{
cout << "Hello, world." << endl;
return 0
}

and heres what i get out:

hello.cpp:3: error '::main' must return 'int'
hello.cpp: in function 'int main()':
hello.cpp:5: error: 'cout' was not declared in this scope
hello.cpp:5: error: 'endl' was not declared in this scope
Compilation failed.

i must've installed 3 or 4 different environments (i have geany installed right now) and i tried it in the terminal too. I even upgraded Ubuntu versions. Please please please, tell me what I'm doing wrong.

As stated before, your book is not a good way to learn programming. It will probably teach you lots of bad programming practices (using system("pause") for example, which is very stupid). Get a good tutorial or a better book: this is a good start: [http://www.cplusplus.com/doc/tutorial/](http://www.cplusplus.com/doc/tutorial/)

---

### Post by zobayer1 on 2011-05-31
Just to add with Petrolea, most of these "old" books (as you used .h) were targeted to VC 6 or Tourbo C 3 or so, many things will differ in gcc / g++.

And from my experience, programming is not meant to be learnt from books... a better way is, when you need to do something, just try to do that with something...

Still if you think of using some books, you can try Herbert Schieldt's Complete Reference.

---

### Post by Petrolea on 2011-06-01
> **zobayer1 said:**
> Just to add with Petrolea, most of these "old" books (as you used .h) were targeted to VC 6 or Tourbo C 3 or so, many things will differ in gcc / g++.

And from my experience, programming is not meant to be learnt from books... a better way is, when you need to do something, just try to do that with something...

Still if you think of using some books, you can try Herbert Schieldt's Complete Reference.

Of course, many things are different now, so are standards. You must get familiar with a basic build of a program and upgrading it will be easier then.

---

