---
title: "GUI with OpenGL"
date: 2008-12-30
forum: Programming Talk
---

### Post by crazyfuturamanoob on 2008-12-30
I want GUI and OpenGL, and I found two ways to have OpenGL+GTK in the same window:
-GtkGLExt
-GtkGLArea

But there's a **huge** problem with both libraries.

With GtkGLExt, I can't use it because it doesn't find it when including.
And yes, I have checked a million times I have the packages installed.
I found out some other people also have the same issue. That's weird.

And I do exactly as GtkGLExt's tiny reference manual says:
[http://gtkglext.sourceforge.net/reference/gtkglext/gtkglext-gtkglinit.html](http://gtkglext.sourceforge.net/reference/gtkglext/gtkglext-gtkglinit.html)
Here's the code:
```

#include <gtk/gtkgl.h>

...

```
And he says:
> 
error: gtk/gtkgl.h: No such file or directory

When I check the place manually, I find gtkgl.h where it should be.
I am supposed to be programming my game, not fixing these issues!

And there are *very* few examples or any help pages for GtkGLExt.
But enough I could do something with it if I'd play around for a while.



So, GtkGLExt does not work. How about GtkGLArea then? No idea.
Because there is not a single tutorial, reference manual, forum thread,**nothing** about it.

I don't even know which library to include! I googled sooo long I thought my head blows.

Just some download links where to download it from.
And it's homepage gives 404, and has been down for a while, according to google.

So I can't use GtkGLArea either because I don't know which header to include, where from, 
or how to use the whole library.



Anybody has a better idea how to mix OGL and GUI? Or maybe tutorials for those libraries? 
Solution for missing GtkGLExt header? Anything?


I originally was making a game. Then a map editor for the game. 
But I can't do anything right now because there doesn't seem to be a way to create the map editor.
And that game was supposed to be a Soldat clone for Linux. Currently it's just lying on my hard drive.
Working map system, physics, textures, water, some basic stuff:

Thanks.

---

### Post by hessiess on 2008-12-30
Wright your own GUI lib which renders using OGL, like Blender for example.

---

### Post by slavik on 2008-12-30
FLTK is a widget toolkit written using OpenGL.

---

### Post by crazyfuturamanoob on 2008-12-30
FLTK is for C++, I use C (and Python).

And writing my own GUI lib... Why to reinvent wheel the 10000th time?

---

### Post by tseliot on 2008-12-30
Maybe you can try [Clutter]("http://www.clutter-project.org/").

---

### Post by bobrocks on 2008-12-30
> **hessiess said:**
> Wright your own GUI lib which renders using OGL, like Blender for example.

Thats a tad excessive for a solution.


The error is because the compiler cant find the header file, gtk/gtkgl.h.  Which I can see you are aware off.  This header file in not in the default search location, /usr/local/include or /usr/include.  It is in a sub directory of the base folder gtkglext or something so gtk/gtkgl wont find it.

**On my computer** to compile a c program using said library I would need to do something like -

```
gcc -I/usr/include/atk-1.0 -I/usr/include/gtkglext-1.0 -I/usr/lib64/gtkglext-1.0/include -I/usr/include/gtk-2.0 -I/usr/lib64/gtk-2.0/include -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib64/glib-2.0/include -I/usr/include/cairo -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/pixman-1  -Wl,--export-dynamic -latk-1.0 -lgdkglext-x11-1.0 -lGLU -lGL -lXmu -lXt -lSM -lICE -lgdk-x11-2.0 -lpangox-1.0 -lX11 -lgdk_pixbuf-2.0 -lpangocairo-1.0 -lcairo -lpango-1.0 -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0 -o hello bob.c
```

for example, now that is a pain in the ... so you can store it in your build file or you can just use pkg-config if you have it installed.

```

gcc `pkg-config --cflags --libs gdkglext-1.0` -I/usr/include/atk-1.0/ -latk-1.0 -o hello bob.c

```


That is how I do it when I'm playing with this stuff, whether that is the best solution or not, I don't know

---

### Post by crazyfuturamanoob on 2009-01-01
Clutter didn't want to compile, it just gave a ton of errors.

But I found GLUI, which is GUI done in pure OpenGL. Perfect for my needs,
except it doesn't compile either. Errors and warnings again :(

Unfortunately newest version of GLUI download link is broken, so I had to grab an older version.

But when I run "make" or "./configure" or anything I could compile it, it doesn't work.

All tools are installed, build-essentials, gcc, everything.


And linking with GtkGLExt didn't work. gcc didn't complain about gtk_gl_init() but it segfaulted.

---

### Post by skullmunky on 2009-01-03
I've used gtkglext a good bit without any problems.  I do recall having to install gtkglextmm from source, so I could use C++; I'm not sure if that's still the case or if it's in the repositories now.

One question - do you want an opengl drawing area inside of a normal GTK application window, with other GTK widgets around it; or do you want something like a fullscreen OpenGL window and the GUI drawn in OpenGL inside it?

If the latter, you could also try Crazy Eddie's GUI, which is used in the Ogre and Irrlicht engines: [http://www.cegui.org.uk/wiki/index.php/Main_Page]("http://www.cegui.org.uk/wiki/index.php/Main_Page")

---

### Post by wdk on 2009-01-03
Try using pkg-config. Compiling gtk and friends usually requires a whole list of libraries too numerous to remember and too tedious to type by hand every time you compile.

Something like this should work:

```
gcc yourprogram.c -o yourprogram `pkg-config gtkglext-1.0 --cflags --libs`

```

If you're curious as to what the output of pkg-config actually looks like, you can type

```
pkg-config gtkglext-1.0 --libs
```

at the command prompt to get a list of the required libraries. These just get appended as arguments to the gcc command.

Remember that the ticks surrounding the pkg-config argument are not your normal single quotes. They are actually backticks which you type using the unshifted "tilde" (~) key. Single quotes will not work.

A makefile might also be something to consider...


I just noticed that bobrocks gave essentially the same answer a few days ago...reading too fast, too late at night I guess...

---

### Post by wdk on 2009-01-03
I don't know if you've resolved the segfault issue with gtk_gl_init(), but you might try calling gtk_init() before calling gtk_gl_init().

My first attempt at a program that only calls gtk_gl_init() and closes gave me a segfault as well. Then I found a nice bit of sample code here:

[http://www.cairographics.org/OpenGL/]("http://www.cairographics.org/OpenGL/") (The "Beef it up a little" example actually uses GtkGlExt)

Here gtk_init() is called before gtk_gl_init(). Adding that to my tiny test program fixed the segfault. It may in your code too.

My sample code (compile using pkg-config as mentioned before):

```

#include <gtk/gtk.h>
#include <gtk/gtkgl.h>

int main(int argc, char ** argv)
{
    gtk_init(&argc, &argv);
    gtk_gl_init(&argc, &argv);

    return 0;
}
```

Good Luck!

---

### Post by crazyfuturamanoob on 2009-01-05
I started writing my own, crappy, hardcoded GUI, which currently has:
[list]
[*]Button, executes given functions on up/down events. Can have a texture overlay.
[*]Text, doesn't do anything but displays text. Very useful.
[*]Typeable textfield, only single line. Adjustable width.
[*]Slider, can return it's position in percents. Adjustable width.
[*]Selectable tab, has sub-widgets which are only active when tab is on top.
[/list]
Button can also be used as a checkbox, with textures, functions and variables.

It isn't very good, and it doesn't have a separate header so it can't be used in any other program.

This sucks but it's easy as eating a pie. No need to mess with linking and compiling.
[SIZE="1"](Except coding, that's not easy, but I only code what I need, to make a map editor for my game.)[/SIZE]

When I have time, I'll read your replies and try out the other GUI toolkits. And I noticed some C++ things there, I use just C.

Also, I found GLUI, which is GUI done entirely in OpenGL. But unfortunately it didn't want to compile and I had to download older 
version because newest versions' download link was broken.

Why any existing ways of combining easy GUI and OpenGL don't work?
I have played, coded, ate, slept, and spent my whole short life on computers, but they just don't like me :(

---

