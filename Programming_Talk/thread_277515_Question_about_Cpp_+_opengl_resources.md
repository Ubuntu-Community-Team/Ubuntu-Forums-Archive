---
title: "Question about Cpp + opengl resources"
date: 2006-10-14
forum: Programming Talk
---

### Post by Wybiral on 2006-10-14
Hello! I just got into Ubuntu a while back (refugee from dreaded "M&M" world) and I've been used to programming with C++ & OpenGL for quite some time. Unfortunately alot of my headers and external files dont work with linux ](*,)

I was wondering if anyone knew of any good image loading headers (hopefully PNG support, as that would be great). Actually, if anyone has ANY ubuntu compatable headers and libs to suggest that would be great. Thanks everyone, I'll probably be seeing you around!

---

### Post by JonahRowley on 2006-10-14
"Image loading headers" doesn't make much sense.  Headers alone don't give you anything, what you really need are libraries.  I've had success with SDL and OpenGL.  It provides cross-platform input and such, and has addon libraries like SDL_Image to handle image loading.  I think there's also a popular library called OpenIL.

---

### Post by Wybiral on 2006-10-14
Well... Actually, you can use headers. I wrote a BMP headers, all you need is a class for loading them. In fact, using SDL for loading my images sounds like overkill since I really only want PNG support. I guess what I'm asking is if anyone has any PNG (or any other well-compressed format) classes to load the images into an opengl compatable format?

---

### Post by JonahRowley on 2006-10-14
> **Wybiral said:**
> I wrote a BMP headers, all you need is a class for loading them.

My point was, headers contain no definitions, only declarations.  You could use libpng, but I find it's easier just to use a library specifically for the task.  It's not really "overkill", it just has more features than you'll need.  Saves time in the end on a menial, boring task.

---

### Post by Wybiral on 2006-10-14
You're right. But I'm going for small output and I only want to include what I am going to use. I'll give that libpng a look, thanks.

btw, headers are mostly used to define classes, and thats really all I need, a class for loading pngs.

---

### Post by JonahRowley on 2006-10-14
> **Wybiral said:**
> You're right. But I'm going for small output and I only want to include what I am going to use. I'll give that libpng a look, thanks.

btw, headers are mostly used to define classes, and thats really all I need, a class for loading pngs.
Yes, but the class itself is not in the header.  Though you can define classes in headers, it's generally considered bad as all methods are automatically inlined and it breaks the compilation process in some cases.  Headers should be used for declaration only.

---

### Post by hod139 on 2006-10-15
> **JonahRowley said:**
> Yes, but the class itself is not in the header.  Though you can define classes in headers, it's generally considered bad as all methods are automatically inlined and it breaks the compilation process in some cases.  Headers should be used for declaration only.

To my knowledge only constuctors are automatically inlined, and if you want to use templates you cannot break apart the declaration and implementation into two files.

As for the original posters question, png's are fairly complicated, so you might be best off using a robust libary like libpng for reading/writing pngs.  Of course, libpng is open source, so if you really want to have the headers/source in your project I suppose you can do that as well (as long as you keep your code open that is).

---

### Post by JonahRowley on 2006-10-15
You *can* break the declaration and implementation files into two:

```

/* template.h */
/* A dummy template class */

template <class T>
class Printer {
  public:
    static void print(T t);
};

```

```

/* template.cc */
#include <iostream>
#include "template.h"

template <class T>
void Printer<T>::print(T t) {
  std::cout << t << std::endl;
}   

int main( int argc, char *argv[] ) {
  Printer<int>::print(10);
  Printer<const char *>::print("hello");
  return 0;
}

```

---

### Post by DavidBell on 2006-10-15
> **JonahRowley said:**
>  Headers should be used for declaration only.

Defining classes in headers is very common. Look at STL, while it's mainly templates I don't think there's anything to say you can't define normal classes in .h. DB

---

### Post by hod139 on 2006-10-15
> **JonahRowley said:**
> You *can* break the declaration and implementation files into two:

```

/* template.h */
/* A dummy template class */

template <class T>
class Printer {
  public:
    static void print(T t);
};

``````

/* template.cc */
#include <iostream>
#include "template.h"

template <class T>
void Printer<T>::print(T t) {
  std::cout << t << std::endl;
}   

int main( int argc, char *argv[] ) {
  Printer<int>::print(10);
  Printer<const char *>::print("hello");
  return 0;
}

```

But this is cheating.  At least with gcc, both the declaration and implementation must be #included.  Taking your example, the following code will not link:
```

#pragma once
/* template.h */
/* A dummy template class */

template <class T>
class Printer {
  public:
    static void print(T t);
};

``````

/* template.cc */
#include <iostream>
#include "template.h"

template <class T>
void Printer<T>::print(T t) {
  std::cout << t << std::endl;
}   
 
``````

/* main.cc */
/*  Note, this will not link using g++ */
#include "template.h"

int main( int argc, char *argv[] ) {
  Printer<int>::print(10);
  Printer<const char *>::print("hello");
  return 0;
}

```

---

### Post by slavik on 2006-10-16
> **hod139 said:**
> But this is cheating.  At least with gcc, both the declaration and implementation must be #included.  Taking your example, the following code will not link:
```

#pragma once
/* template.h */
/* A dummy template class */

template <class T>
class Printer {
  public:
    static void print(T t);
};

``````

/* template.cc */
#include <iostream>
#include "template.h"

template <class T>
void Printer<T>::print(T t) {
  std::cout << t << std::endl;
}   
 
``````

/* main.cc */
/*  Note, this will not link using g++ */
#include "template.h"

int main( int argc, char *argv[] ) {
  Printer<int>::print(10);
  Printer<const char *>::print("hello");
  return 0;
}

```
it actually will if you do 'g++ main.cc template.cc' :) btw, I am not sure if that is the proper command since I am used to Anjuta generating the proper makefile for me :P

BTW, I have to say that I am guilty of putting an entire class into a .h file, but this was done to keep things simple (maybe later I will make a static/dynamic library out of it).

---

### Post by JonahRowley on 2006-10-16
That g++ command is more or less correct.  Oh, and about the **#pragma once**, a different, but more or less the same, method is used on Linux (since no pragmas are standard).

```

/* some_header.h */
#ifndef SOME_HEADER_H_INCLUDED
#define SOME_HEADER_H_INCLUDED

/* ... */

#endif

```

---

### Post by hod139 on 2006-10-16
> **slavik said:**
> it actually will if you do 'g++ main.cc template.cc' 
No it wont:
```

g++ main.cpp template.cpp
/tmp/cceWa1Yx.o: In function `main':main.cpp:(.text+0x24): undefined reference to `Printer<int>::print(int)'
:main.cpp:(.text+0x30): undefined reference to `Printer<char const*>::print(char const*)'
collect2: ld returned 1 exit status

```Like I said, with gcc, both the declaration and implementation of templated classes must be #included.

[quote=JonahRowley]Oh, and about the **#pragma once**, a different, but more or less the same, method is used on Linux (since no pragmas are standard).[/quote]
You are correct that using macro based include guards is how the standard states to do it, and with early versions of gcc you would get a warning (error?) since gcc wanted to push standards compliance. However, since version 3.4, gcc has  un-depreciated the use of #pragma once.  I like to use it because it looks cleaner, and some people even claim code compiles faster since it avoids a symbol lookup.  So yes, the code I wrote is correct (but not standards compliant) on modern versions of linux using the a recent build of gcc.  However, it is not very portable, since it won't work on older versions of the gnu compiler, or a more standards compliant compiler.

I would also like to add, #pragma once was not a Microsoft invention.  It was a GNU creation, then deemed obsolete, then many other compilers started supporting it, and now GNU supports it again!

---

