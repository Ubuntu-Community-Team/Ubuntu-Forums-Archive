---
title: "current openGL tutorials?"
date: 2008-03-09
forum: Programming Talk
---

### Post by ZeroHimself on 2008-03-09
ok.... just trying to get my linux programming game on here..... I can use direct X, I've gotten sdl, opengl, glut, etc.... searched for some tutorials, and ***NONE WILL COMPILE!!!!!***, whats up with this???? I can't seem to find any working tutorials when searching google...  any one know of any *WORKING* and *UP TO DATE* tutorials....(goal is to write a *SEMI*-portable(ie with minor modifications) game demo):confused:

---

### Post by lnostdal on 2008-03-10
"none will compile" doesn't mean anything to people reading your post .. this time you are the compiler spitting out (to us) meaningless error messages .. could you instead take the role of a proxy and forward the transcript of your dialog with the compiler directly?

edit:
PS: you'll get extra points for including a short short code sample that triggers your problem

---

### Post by Wybiral on 2008-03-10
[NeHe]("http://nehe.gamedev.net/") is the best place for OpenGL examples. My guess is that you're compiling it wrong (probably not linking to the binaries or you don't have the development files installed)... But I can't tell since you haven't posted any examples.

---

### Post by moma on 2008-03-10
Hello,

Check [this guide....]("http://ubuntuforums.org/showthread.php?p=3627418&posted=1#post3627418")
And read notes 1), 3) and 5) carefully.

---

### Post by ZeroHimself on 2008-03-10
well, i've installed everything needed(at least according to a few different guides), including: freeglut, libsdl, etc.... I am using code::blocks, and it appears to work, i have the proper headers in /usr/include/GL/ , and included them in my c++ file
like this:
```

#include <stdio.h>   // Always a good idea.
#include <time.h>    // For our FPS stats.
#include <GL/gl.h>   // OpenGL itself.
#include <GL/glu.h>  // GLU support library.
#include <GL/glut.h> // GLUT support library.
#include <stdlib.h>
#include <string.h>

/* lots of extra non-relavent stuff..... */

// following code produces "undefined reference to 'glutBitmapCharacter'" when compiled
glutBitmapCharacter(font,*str++);
/* more stuff.......
....
...
*/
// following cod produces "undefined reference to 'glEnable'"

   if (Texture_On)
      glEnable(GL_TEXTURE_2D);
   else
      glDisable(GL_TEXTURE_2D);

/* more stuff...., etc */

// many more *very similar* errors occur


```

as i am new to open gl, code::blocks, sdl, and glut, i don't understand where the problem is....
the headers are there...., and stuff like "GL_TEXTURE_2D" seem to exist....
so how are the gl and glut function calls not defined???
any ideas?

---

### Post by lnostdal on 2008-03-10
heh, these are just normal linker errors .. you are just including headers (compile time) .. how do you run the linker?

---

### Post by lnostdal on 2008-03-10
why don't you learn how things work properly from the ground up? .. start with understanding the compilation and linking process .. maybe [http://www.network-theory.co.uk/docs/gccintro/gccintro_82.html](http://www.network-theory.co.uk/docs/gccintro/gccintro_82.html) gives a good overview

---

### Post by ZeroHimself on 2008-03-10
it does seem to be a linker problem.... in test.o ..  so, what exactly does this mean.... my educated guess is that i have the headers installed, but not the library files, so the linker cannot link it all together....

if this is correct, how do i get the lib files included in the link process??

i would have thought that when i installed my lib's and such with apt-get that it would have taken care of all of this....
or maybe it's a problem with my code::blocks configuration??

---

### Post by lnostdal on 2008-03-10
nono, there are many, many libraries installed on your system .. often there are multiple versions of the same library .. so you have got to tell gcc(#1) which libraries it is to link to and where it can find them

[http://www.network-theory.co.uk/docs/gccintro/gccintro_8.html](http://www.network-theory.co.uk/docs/gccintro/gccintro_8.html)
..and further: 
[http://www.network-theory.co.uk/docs/gccintro/gccintro_17.html](http://www.network-theory.co.uk/docs/gccintro/gccintro_17.html)

(see how *undefined reference to `sqrt'* show up in the example there .. same thing you're dealing with)


#1: or, you have got to tell your IDE/editor to tell gcc for you

---

### Post by ZeroHimself on 2008-03-10
ahh, i see, i found my answer, it was the configuration of my ide, it didn't know where to look for my GLUT installation.....
got it to compile, but it wouln't run..... i get an "ld" error now, it can't find xf86vm ...

oh well, i can figure this out.....
but i might as well ask

as for starting from the ground up(i know very little about c++ on a *nix environment), do you know of any *all i  need to know* guides for gcc, heck, really just the whole development process under linux....(openGL would be nice too, seeing as how i am coming from a Dx9 system)

but thank you very much for all of your help ;0

---

### Post by Wybiral on 2008-03-10
If you really want to get to know GCC, don't use an IDE. Start in the command-line with a text editor. You will understand GCCs warnings and errors more if you have to pass the flags/arguments to it yourself.

EDIT:

Also, that code you posted is C, not C++. Be careful not to mix those two up when you're learning (there is a big difference).

---

