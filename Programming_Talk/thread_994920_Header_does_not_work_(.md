---
title: "Header does not work :("
date: 2008-11-27
forum: Programming Talk
---

### Post by crazyfuturamanoob on 2008-11-27
I managed to do this header for my graphics library(?) graphics.c:
```

// graphics.h

SDL_Surface *surface;

int initGL( GLvoid );

int resizeWindow( int width, int height );

struct glTEX
{
    GLuint data;
    int width, height;
};

struct glTEX LoadTexture( char filename[]);

void draw_texture( struct glTEX *texture, float x, float y );
void draw_texture_centered( struct glTEX *texture, float x, float y );

```
I got this error, but I don't think it's anyhow related to graphics.c so I don't post it.
> 
graphics.h:15: error: stray &#8216;\240&#8217; in program

What is stray 240? What's wrong? O.o

And SDL & OpenGL libs are included in the main program, so it isn't necessary to include them in graphics.c/h

---

### Post by monkeyking on 2008-11-27
Try posting a link to your original file.
Are you using unicode?
Have you copy-pasted some of your code from the internet?

Try open it in vim and save it.
I've had success using vim to save in the current charsetformat.


also  try to do a 

unix2dos followed by a dos2unix.

---

### Post by crazyfuturamanoob on 2008-11-27
> **monkeyking said:**
> Try posting a link to your original file.
Are you using unicode?
Have you copy-pasted some of your code from the internet?

Try open it in vim and save it.
I've had success using vim to save in the current charsetformat.


also  try to do a 

unix2dos followed by a dos2unix.

Both terminal and vim ignored "unix2dos" and "dos2unix". And I wrote that header myself, copied nothing from anywhere.

---

### Post by monkeyking on 2008-11-27
The compiler complains, that your sourcecode contains a symbol it doesn't recognince.


you have to have the package
tofrodos installed for using dos2unix

But take a look at your sourcecode at line 15, and check for hidden stuff.
Try deleting the line and rewrite it.

---

### Post by dwhitney67 on 2008-11-27
> **crazyfuturamanoob said:**
> ...

And SDL & OpenGL libs are included in the main program, so it isn't necessary to include them in graphics.c/h

Hopefully by now you have solved the stray character problem.

It appears that you do not have dos2unix installed on your system (or maybe you do?)

Anyhow, a "library" is generally composed of one or more header files and one or more library files (which contain code that has been pre-compiled for your use).

Just because you include SDL and openGL files in your main module does not mean that they are not needed elsewhere.

Looking at the graphics.h file you posted, it is given that you will need to include the appropriate SDL and openGL header file(s) in your file.  When you implement your functions in graphics.c, then you will *not* be required to include these.  But obviously, you will need to include graphics.h.

The best practice to follow when including header files is to include those header file(s) that are local to the directory where your source code resides, then include those header file(s) that may be commonly used throughout your project, and then follow these by including any 3rd-party header files (e.g. SDL.h, stdio.h, etc.).

The rationale for this is to ensure that your (and your project's) header files can stand on their own, without any missing dependencies.

You should also wrap the statement(s) in your header file with the multiple-inclusion guard statements.  For example:
[php]
#ifndef GRAPHICS_H
#define GRAPHICS_H

// your function prototypes (and, sigh, global variables)

#endif
[/php]

---

### Post by wmcbrine on 2008-11-27
Weird. What editor did you use?

\240, that's octal, so 160 decimal... that's a non-breaking space. Which is why you can't see it...

---

### Post by crazyfuturamanoob on 2008-11-27
> **wmcbrine said:**
> Weird. What editor did you use?

\240, that's octal, so 160 decimal... that's a non-breaking space. Which is why you can't see it...

But ASCII has only 127 symbols! 160?? How is that possible?

Edit: After rewriting the line, it works. And I use scite.

Edit2: Does it matter if I have two prototypes of same function?

Edit3: When trying to compile, my main program does not find the function definitions in graphics.c, 
but it does find glTEX definition (not complaining about it). Should I include graphics.c in the header too?

---

### Post by dwhitney67 on 2008-11-27
What are the names of your files?

For now, I will assume you have a file called graphics.h, another file called graphics.c, and another called main.c.

Assuming graphics.h has function prototypes (definitions) in it, then this needs to be included within _all_ .c files that call upon those functions.

When compiling, all that needs to be specified on the gcc command line is graphics.c and main.c.

---

### Post by wmcbrine on 2008-11-27
> **crazyfuturamanoob said:**
> But ASCII has only 127 symbols! 160?? How is that possible?Your editor isn't limited to ASCII.

BTW...

> *And SDL & OpenGL libs are included in the main program, so it isn't necessary to include them in graphics.c/h*As I mentioned recently in another thread, you *include* header files, and you *link* libraries. It sounds like you may not be clear on the difference. Inclusion ("#include <file.h>") needs to be done (directly or indirectly) in each and every file where the functions are referenced. Linking ("-lfile") is what's done only once.

---

### Post by dribeas on 2008-11-27
> **wmcbrine said:**
> Inclusion ("#include <file.h>") needs to be done (directly or indirectly) in each and every file where the functions are referenced. Linking ("-lfile") is what's done only once.

My suggestion has always been including all headers that would be required directly. In some contexts it is common to have indirect includes, but I recommend against it as a change in an external header will render your own header useless.

Assume, for example, that a.h includes z.h, and that your header b.h requires a declaration from z.h. Even if it includes a.h it should also include z.h. Else, a later change in a.h (if it no longer requires declarations from z.h) will break all the code that uses your header.

---

