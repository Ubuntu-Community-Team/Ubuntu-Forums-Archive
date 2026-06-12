---
title: "Help understanding libraries"
date: 2008-07-01
forum: Programming Talk
---

### Post by DeathOnJuice on 2008-07-01
This year, I took a high school computer science class in Java, but I'm really not sure that I learned much. I knew most of it from a minimal programming background. For a summer project, I'm going to try to learn a new language (C or Python, haven't done much yet) in greater depth than a normal high school course.

One thing that I have always been a bit confused about are libraries. I know that they allow you to incorporate pre-made functions into your programs... But that's about it. We never heard the word library in computer science. I install them all the time to compile some games (as in freeglut3, freeglut3-dev), but I really don't have a clue behind a lot of terminology.

Could you explain some of these for me? Better, to save yourself from all the work, just link a very newbie-friendly guide to libraries. These are just a couple questions off the top of my head. Should be enough of a start for me to understand everything about libraries, though...

1. If a ____-dev (i.e. freeglut3-dev) packages lets you compile programs, what does the normal freeglut3 package do? What are the differences between them?
2. How exactly do bindings work? I know they have something to do with allowing different languages to use the same library.
3. Where are libraries stored? In a C++ program, I believe you can just type #include <GL/glut> or something to that effect. How does it find that?
4. Finally, explain the differences between the usage of OpenGL, SDL, and something like, say, PyGame.
5. What are headers?

Thanks. I hope this all makes sense.

---

### Post by LaRoza on 2008-07-01
> **DeathOnJuice said:**
> 
1. If a ____-dev (i.e. freeglut3-dev) packages lets you compile programs, what does the normal freeglut3 package do? What are the differences between them?

The normal binary package is what is used by a running program. It is a shared library.

> 
3. Where are libraries stored? In a C++ program, I believe you can just type #include <GL/glut> or something to that effect. How does it find that?

No, that is just the header. In /usr/include/ usually.

The actual libraries are in /lib (usually)

They are shared libraries and can be used by any program. The header files just allows you to compile.

> 
4. Finally, explain the differences between the usage of OpenGL, SDL, and something like, say, PyGame.


When you are using OpenGL you are using OpenGL, when you are using SDL you are using SDL and when you are using PyGame you are using PyGame (which uses SDL).

What exactly are you asking? OpenGL and SDL are often used together. My wiki will have information on them. PyGame is a module for Python that uses SDL.

---

### Post by DeathOnJuice on 2008-07-01
> **LaRoza said:**
> The normal binary package is what is used by a running program. It is a shared library.

They are shared libraries and can be used by any program. The header files just allows you to compile.

I thought that once a program was compiled, all the libraries it needed would be integrated into the executable? Surely you don't need these libraries on every computer on which these programs are run. Unless... Are they for interpreted languages?

Oh, I forgot to ask: What are headers?

As for the question about OpenGL, SDL, and PyGame, forget about it. I guess I'll learn the functions of those when I actually begin to use them. It's just that I know that SDL uses OpenGL and PyGame uses SDL, but how they use each other I don't know.

---

### Post by LaRoza on 2008-07-01
> **DeathOnJuice said:**
> I thought that once a program was compiled, all the libraries it needed would be integrated into the executable? Surely you don't need these libraries on every computer on which these programs are run. Unless... Are they for interpreted languages?

No. It can be statically linked but that makes a program very large and it is only used for certain types of programs.

> 
Oh, I forgot to ask: What are headers?

I suggest you learn how to program, to find out these answers. My wiki may be helpful.

---

### Post by DeathOnJuice on 2008-07-01
> **LaRoza said:**
> 
I suggest you learn how to program, to find out these answers. My wiki may be helpful.

Yikes, that's no good :D . For the record, I do know how to program somewhat - either Java has no headers, or my class was REALLY bad.

But you're right; jumping into C will probably answer most of these questions.

---

### Post by NathanB on 2008-07-01
Static Library -- ( "*.lib" in Windows; "*.a" in Linux ) If you use any of the functions within, those functions -- and *only* those functions that you actually use -- will be linked into your final executable.

Dynamic (Shared) Library -- ( "*.dll" in Windows; "*.so" in Linux ) These functions are not included into your executable.  Your application will request these functions at load-time and the loader will find (and load the library if it isn't already in memory) and make sure these functions are available before your application starts.

Header File -- contains mostly:
    -  prototypes: tells the compiler and linker that these functions are externally supplied; how many and what type of parameters; return type; etc.

    -  macros: wrappers around functions, etc.

    -  structure definitions

    -  constant definitions

For more info:  [http://en.wikipedia.org/wiki/Library_(computing](http://en.wikipedia.org/wiki/Library_(computing))

Nathan.

---

### Post by pmasiar on 2008-07-01
Learn Python (see my sig).

Python will let you understand basic concepts of programming without forcing you to handle too many secondary details, like object type, exceptions, etc.  With your basic Java, you should be able to pick Python syntax in a week or two max, and start solving simple training tasks, like Project Euler.

Library is just code to solve some problems you need to solve repeatedly - move code to the library, call it from there. In Python, it is trivial.

---

### Post by LaRoza on 2008-07-01
> **DeathOnJuice said:**
> Yikes, that's no good :D . For the record, I do know how to program somewhat - either Java has no headers, or my class was REALLY bad.

But you're right; jumping into C will probably answer most of these questions.

Java does it differently. Java is a platform and is setup differently than many languages.

Java doesn't have a C style header, as far as I know. 

Without any C knowledge, it will be hard to explain in full, but basically a header contains information about functions; but no code that is compiled (sort of).

So if all the SDL code is the library compiled and ready to be linked, the compiler doesn't know what the SDL functions look like without a header telling it how to compile before it is linked.

Here is an example of what a header file may contain:
```

int post(int,char*);
double getPostCount(char*);

```

As you can see, it contains only the prototypes of functions so the compiler knows that the function "post" returns an int and accepts an int and a string as arguments. (The header isn't written like it would be in real life)

---

### Post by NathanB on 2008-07-02
> **LaRoza said:**
> Here is an example of what a header file may contain:


A really good example can be found on the standard Ubuntu file system:

/usr/include/X11/Xlib.h

Nathan.

---

### Post by LaRoza on 2008-07-02
> **NathanB said:**
> A really good example can be found on the standard Ubuntu file system:

/usr/include/X11/Xlib.h

Nathan.

Yeah, but I wanted to make it make some sense to a Java programmer. :-)

---

### Post by snova on 2008-07-02
I'm usually quite adept at explaining things. Perhaps I can help.

A library is a file in which executable code is placed. They come in two forms:

[LIST]
[*]Static libraries
[*]Shared libraries
[/LIST]

A static library, when linked with the program, is fully incorporated. This makes the program bigger, but then it won't depend on the shared library to exist.

Shared libraries are used differently. The finished executable doesn't contain the code, but merely a reference to the library. When your program is run, Linux loads the additional libraries into memory and performs some complex process about which I know little- but the end result is that your program can use the code anyway.

To answer your question about packages, the libX package contains the shared libraries for the X library, and the libX-dev package contains headers, and sometimes static libraries.

A header contains information about a library, or a portion of the library. Very large libraries can have hundreds of headers. But they all do the same thing: they define the API that the library exposes.

(API = Application Programming Interface, or the interface a library supplies to programs that use it. A library should only be accessed through this interface.)

Typically, you'll find function declarations in headers. If these were incorrect (say, the header declaration had an extra parameter that the real function doesn't), your program would crash almost instantaneously. Hence their use.

A "binding" is the glue that makes two different programming languages interoperate with each other. This is necessary because, for example, a Python script cannot use C headers, nor vice versa.

You said to ignore your question about OpenGL, SDL, and PyGame, but I know that answer to that to:

OpenGL is a graphics library. It is comparable to Microsoft's DirectX, but better depending on who you ask :)

OpenGL is for 3D graphics, and absolutely nothing else. SDL is another library with additional functionality for things like joysticks, CD drives, input, and so on.

PyGame is a set of bindings that make SDL accessible from Python (because SDL is written in C).

The library paradigm I just described is not entirely accurate for different programming languages. In Python, and in many other languages, the library IS the API. If you install the files needed to use a library, you essentially have the -dev package already.

Libraries are stored in all sorts of places. The crucial ones (if the system can't operate or even boot up without them, they are considered "crucial") are stored in /lib. The less important ones (i.e. all the rest) are in /usr/lib. The ones you install yourself are in /usr/local/lib.

C is a very low level language (though when you mess with the stuff that I do, C looks positively charming. Ever messed with GDT's? ](*,)). If you are only just beginning though, I suggest Python instead.

I hope I helped. Enjoy programming.

---

### Post by DeathOnJuice on 2008-07-03
That was a huge help. I'm pretty sure I grasp all of those concepts now.

Last question; let's move out of theory and into practice. I know that both OpenGL and SDL(/Pygame) do graphics. I also know that if you use OpenGL for graphics, you still need SDL for input, etc.

Suppose that I want to make a small, 2D application in Python, just to say I've done something graphical. Pretty random - I'm thinking that you can place sprites, and have them smoothly slide to locations you clicked. Obviously I will use SDL/Pygame for input. Should I use SDL/Pygame or OpenGL for the actual graphics?

That will wrap it up. Once again, thanks for all the help.

---

### Post by LaRoza on 2008-07-03
> **DeathOnJuice said:**
> 
Suppose that I want to make a small, 2D application in Python, just to say I've done something graphical. Pretty random - I'm thinking that you can place sprites, and have them smoothly slide to locations you clicked. Obviously I will use SDL/Pygame for input. Should I use SDL/Pygame or OpenGL for the actual graphics?


PyGame can handle that.

---

### Post by DeathOnJuice on 2008-07-03
That's good. I'd rather wait on OpenGL until 3.0 comes out, anyway.

---

