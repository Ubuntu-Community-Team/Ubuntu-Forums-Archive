---
title: "Error in Hello World program!?! C++"
date: 2006-12-25
forum: Programming Talk
---

### Post by navneeth on 2006-12-25
This is probably the strangest thing I've seen...I get errors when the hello world program is compiled. I have installed g++.

Here's what I started with:

```
#include <iostream.h>

void main()
{
    cout << "Hello World!";
}

```

(I tried with both 'main' and 'void main')
 
This is the error message I got:

> In file included from /usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../include/c++/4.1.2/backward/iostream.h:31,
                 from hello.cc:1:
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../include/c++/4.1.2/backward/backward_warning.h:32:2: warning: #warning This file includes at least one deprecated or antiquated header. Please consider using one of the 32 headers found in section 17.4.1.2 of the C++ standard. Examples include substituting the <X> header for the <X.h> header for C++ includes, or <iostream> instead of the deprecated header <iostream.h>. To disable this warning use -Wno-deprecated.


And when I remove the 'h' from iostream.h, I got:

> hello.cc: In function ‘int main()’:
hello.cc:5: error: ‘cout’ was not declared in this scope


I have tried using tested programs from the net, but the result is the same.  I even tried renaming the extension (cc, cpp, c++).

Any ideas?

---

### Post by Verminox on 2006-12-25
"cout" is an object in the namespace "std".

Either try:

```
std::cout << "Hello, World!";
```


or the "using" keyword to tell the compiler that you are using a particular namespace. eg.

```
using namespace std;
cout << "Hello, World!";
```

---

### Post by navneeth on 2006-12-25
Thanks.  std::cout works, but I see many programs without it. [http://www.roesler-ac.de/wolfram/hello.htm#C++](http://www.roesler-ac.de/wolfram/hello.htm#C++) 

 Is it required by the latest vresion of the compiler or something like that?

---

### Post by engla on 2006-12-25
yep, your hello world code is wrong, and I don't know what but some windows environment seems to do "using namespace std" by default.

here's a better version from wikibooks:
```

#include <iostream>
 
int main()
{
    std::cout << "Hello, world!" << std::endl;
    return 0;
}

```
note that main must return int.

---

### Post by Jucato on 2006-12-25
One of the problems in your code is #include <iostream.h>. Standard C++ doesn't declare standard header files like that. Instead they used #include <iostream> only (no .h).

Another problem, although not stated in the error message you posted, is that you didn't use the proper namespace for cout and endl. The proper way to use those would be engla's example.

---

### Post by po0f on 2006-12-25
navneeth,

The thing with finding C++ tutorials on the internet is that some of them might come from before C++ was standardized or they might not be too clear if they are targeted at Windows developers and not more generic, C++98 (the standard) programming.  I found the [Thinking in C++](http://mindview.net/Books/TICPP/ThinkingInCPP2e.html) books to be good introductions to standard C++ programming (there are no vendor-specific details in it).

---

### Post by navneeth on 2006-12-26
Thanks for the helpful comments, guys, and, po0f, thanks for the link. 

I'm just a beginner, and I think the book I use for a course may be seriously outdated.

---

### Post by po0f on 2006-12-26
navneeth,

Most college books tend to be.  ;)

---

### Post by Desi-Tek.com on 2006-12-26
i learned c++ from cplusplus.com best online turorial on c++

---

