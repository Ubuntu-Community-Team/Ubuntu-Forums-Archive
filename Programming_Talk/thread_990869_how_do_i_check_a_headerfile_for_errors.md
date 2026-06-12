---
title: "how do i check a headerfile for errors?"
date: 2008-11-23
forum: Programming Talk
---

### Post by jimi_hendrix on 2008-11-23
how do i check a headerfiles for errors?

---

### Post by Zugzwang on 2008-11-23
Well, for searching for syntactic error, you can try to compile the following program:

[PHP]
#include "yourheaderfile.h"

int main() {
   return 1;
}
[/PHP]

If this doesn't work, then the error is in your header file since the rest is trivial.

Also, why do you need to do that? When compiling something that uses the header file, you'll get references to the errors anyway, right?

----

Or do you mean how to check that the "header file" does what it is supposed to do?

---

### Post by nvteighen on 2008-11-23
Zugzwang is right... but moreover, what header file do you suspect to have an error? If it is some Standard Library's header or another common library's, forget it and better look at your source.

---

### Post by jimi_hendrix on 2008-11-23
@nvteigh...

i wrote my own header and i want to check it for errors

---

### Post by jimi_hendrix on 2008-11-23
just tried it...thats a lot of errors...

---

### Post by jimi_hendrix on 2008-11-23
ok problem...in my makefile i tell the compiler: -lSDL_ttf

but when i do make i get an error saying SDL_ttf does not exist...but when i do pacman -Qs SDL_ttf it says its installed (i use arch)

any ideas?

---

### Post by geirha on 2008-11-23
Do you see the library with this?
```
ldconfig -p | grep SDL
```

Also, check where the package installs the library. I don't know pacman, but it probably has a way of listing installed files of a package.

---

### Post by nvteighen on 2008-11-23
> **jimi_hendrix said:**
> @nvteigh...

i wrote my own header and i want to check it for errors

What have you written to your header? Header files should **not** include any implementation code, just prototypes (in other words, just interface).

> **jimi_hendrix said:**
> ok problem...in my makefile i tell the compiler: -lSDL_ttf

but when i do make i get an error saying SDL_ttf does not exist...but when i do pacman -Qs SDL_ttf it says its installed (i use arch)

any ideas?

Probably you only have the library installed, but not the development package. I don't know how you do that in Arch, but in Debian/Debian-based you'd install the *-dev package.

---

### Post by jimi_hendrix on 2008-11-23
> **nvteighen said:**
> What have you written to your header? Header files should **not** include any implementation code, just prototypes (in other words, just interface).

i went through the lazyfoo SDL tutorial and pulled out all the classes and functions i thought i would need a lot
> 
Probably you only have the library installed, but not the development package. I don't know how you do that in Arch, but in Debian/Debian-based you'd install the *-dev package.

searched the arch repo and AUR and found no -dev so i will get help via irc

---

### Post by nvteighen on 2008-11-23
> **jimi_hendrix said:**
> i went through the lazyfoo SDL tutorial and pulled out all the classes and functions i thought i would need a lot


Hmm... You should copy those to a cpp source code (I assume this is C++ since you mention classes) and write a header using the prototypes...

If there's an error, the compiler will tell you when compiling the modules together.

---

### Post by jimi_hendrix on 2008-11-23
...great another hours work after i fix all the bugs when i included it...

my bugs seem to be mostly definition errors...some of which boggle me

---

### Post by jimi_hendrix on 2008-11-23
if i put the prototypes of all my functions at the top, but i have

int a();
int b();

then i have in the real code
int b()
{
return a();
}

int a()
{
return 0;
}



is that legal?

---

### Post by geirha on 2008-11-23
Yes, that's perfectly legal.

---

### Post by jimi_hendrix on 2008-11-23
what if i swapped the a() and b() prototypes so they were like

b();
a();

but the definition of the functions were the same?

---

### Post by geirha on 2008-11-23
It will still work. The prototypes tell the compiler that you want to use two functions, a and b that return ints. At any point below those prototypes, you can use those functions as long as you define those functions at some point in the code. The order does not matter, as long as the prototypes appear before you attemt to call the functions.

---

### Post by jimi_hendrix on 2008-11-23
why cant i put the prototypes and definitions of my functions in the same header?

---

### Post by geirha on 2008-11-23
You can if you only include the header file in one .c-file (though bad practice). If you include it from more than one .c-file from the same program, you will define the same functions several times, which is not legal in C.

---

### Post by jimi_hendrix on 2008-11-23
can you show me how to do it the right way then...even though i will only need this header in one file normally

---

### Post by geirha on 2008-11-23
Ok, here we put your two functions a and b into myfuncs.c, declare them in myfuncs.h, then include myfuncs.h in another .c-file (main.c) for use.

myfuncs.h:
```

#ifndef MYFUNCS_H
#define MYFUNCS_H

int a();
int b();

#endif

```

myfuncs.c
```

#include "myfuncs.h"

int a() { return 0; }
int b() { return a(); }

```

main.c:
```

#include <stdio.h>
#include "myfuncs.h"

int main()
{
    printf("a: %d\n", a() );
    printf("b: %d\n", b() );
    
    return 0;
}

```

```

$ gcc -c main.c myfuncs.c  # compile
$ gcc main.o myfuncs.o     # link
$ ./a.out
a: 0
b: 0
$ gcc main.c myfuncs.c     # alternatively compile and link in one go

```

---

### Post by jimi_hendrix on 2008-11-23
whats the preprocessor stuff in the header?

---

### Post by skullmunky on 2008-11-23
usually you do it like this:

```

// awesome.h

int a ();
int b ();

```

```

// awesome.cpp 

#include "awesome.h"
int a ()
{ 
  return b();
}

int b()
{
 return 0;
}

```


There are two reasons not to only put implementation in the .cpp (or .c or .cxx or what-have-you) and not in the header.

1. problems if you include from multiple files
2. longer compiles - when you have a project with multiple source files, and you just change one of them, then often only that bit has to get recompiled.  if everything is in the headers it ALL gets recompiled every time.  
3. for understanding your code you can just look at the .h file quickly to see what the functions are and what arguments they take, etc.  when I use other ppls' code without a lot of documentation I often just go back and read the header files.  if all the code is in there too it's harder to do that.
4. if you make a library that other people will use, you can give them the compiled library (the .so) and the header (.h) and they can successfully link your library in.  they don't need all the source code in your library and don't have to recompile all of it.

SDL, for example.  when you compile something using SDL, you just have to #include sdl.h, the header with the declarations of the functions and then link to the already-compiled libsdl.so.  

when you -do- have multiple source files, there is another thing you have to do.  if a header is going to get included multiple times, you'll get an error because each time it gets read the compiler tries to redefine the function but it already exists.

so you often do this:

```

// awesome.h

#ifndef _AWESOME_
#define _AWESOME_

int a ();
int b ();

#endif

```

so the first time through it defines the macro _AWESOME_ ; next time it gets included the macro's already defined so it just skips the whole file.

---

### Post by geirha on 2008-11-23
It's to avoid the header file being included more than once. It won't happen in this case, but it's good practice to always add it. To give an example, let's say you have another header file, other.h, that includes myfuncs.h. Then, if you include both other.h and myfuncs.h in main.c, then myfuncs.h will be included twice. Without the preprocessor stuff you'll get an error since the code in myfuncs.h will be run twice. 

With the preprocessor stuff, the first time it is included, MYFUNCS_H will be defined, and the next time it is included, everything between the #ifndef and #endif will be removed, basicly including an empty file.

---

