---
title: "search path problem"
date: 2012-07-16
forum: Programming Talk
---

### Post by JoseJesus on 2012-07-16
Hello, I'm a newbie to linux programming. I want to program in C with GTK.
 Working with CodeBlocks, libgtk2.0-dev installed.
 When compiling a test code I get a message error <gtk / gtk.h> file or directory does not exist.
 By manually search for this file, I find that at <user/include/gtk-2.0/gtk/gtk.k>, because that, i enter the directory  <gtk-2.0> in compiler search path list on CodeBlocks.
 New build, new error, now within  <gtk.h>  # include<gio/gio.h>. I found this file in <user/include/glib-2.0/gio/gio.h>. ,problem <glib-2.0> not reconized
 My solution does not solve the problem, there must be another way. Can anyone help? thank you

---

### Post by trent.josephsen on 2012-07-16
This kind of thing is one reason I don't advise newbies to start with C. You have an admirable goal but you're going about it wrong IMNSHO.

Running `pkg-config --cflags gtk+-2.0` should give you the flags you need to pass to gcc in order to compile it properly. (Somebody correct me if I've got the wrong package name.) For me, on Arch, it gives the following; yours may be different but that's why pkg-config exists to begin with.

```
$ pkg-config --cflags gtk+-2.0                   
-pthread -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/gdk-pixbuf-2.0 -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/libpng15
```

But you don't have to type out that whole thing; just interpolate it into the gcc command line with the shell:

```
$ gcc program.c $(pkg-config --cflags gtk+-2.0)
```

This takes care of the compiler flags; to link properly you'll also want to add --libs after --cflags.

As for putting all this information into CodeBlocks, well, good luck.

---

### Post by JoseJesus on 2012-07-19
Thanks for the help. I understand what the problem

---

### Post by JoseJesus on 2012-07-19
Ok thanks for the reply my friend
now i have tested your advice but the problem continue
in diferent way. 

if i type this command in console pkg-config --cflags gtk+-2.0
i get a list path in response.

then i make somo modification on CodeBlocks compiler DialogBox
this is the old makro
$compiler $options $includes -c $file -o $object

the new one (without parentheses)

$compiler $options $includes -c $file -o $object $pkg-config --cflags gtk+-2.0

also i try
$compiler $options $pkg-config --cflags gtk+-2.0 -c $file -o $object 
in both cases i get this message
can you show me the way?

-------------- Build: Debug in gtkapi ---------------

Compiling: sound_test_c.cpp
g++: erro: gtk+-2.0: Ficheiro ou directoria inexistente
g++: erro: unrecognized option &#8216;-config&#8217;
g++: erro: unrecognized option &#8216;--cflags&#8217;
Process terminated with status 1 (0 minutes, 0 seconds)
0 errors, 0 warnings

---

### Post by trent.josephsen on 2012-07-19
I don't know if what you want to do, which is run `pkg-config --cflags gtk+-2.0` and put the output in the command line of gcc, is actually possible in CodeBlocks; I've never used CB. But what you can do is take the *output* of the command and copy-paste it directly into the command line.

Overall, you should probably find out how people usually do this kind of thing in CodeBlocks and not listen to whatever nonsense I have to say.

---

### Post by JoseJesus on 2012-07-19
Ok. Another friend said

pkg-config is not a C::B macro and can not be used this way.

Just add `pkg-config --cflags gtk+-2.0` to the projects build options tab "Compiler settings -> Other options" and `pkg-config --libs gtk+-2.0` to "Linker settings -> Other linker options".
Note the backticks ( "`" )!

but i get the same error message

since quitting smoking until my head
 but do not give up easily

but if i type pkg-config --cflags gtk+-2.0 in console i get the list path of gtk pak
jose@jose-F3F:~$ pkg-config --cflags gtk+-2.0
-pthread  -I/usr/include/gtk-2.0 -I/usr/lib/i386-linux-gnu/gtk-2.0/include  -I/usr/include/atk-1.0 -I/usr/include/cairo  -I/usr/include/gdk-pixbuf-2.0 -I/usr/include/pango-1.0  -I/usr/include/gio-unix-2.0/ -I/usr/include/glib-2.0  -I/usr/lib/i386-linux-gnu/glib-2.0/include -I/usr/include/pixman-1  -I/usr/include/freetype2 -I/usr/include/libpng12 

strange! I think the compiler expects the truck from the include directory, and I now see that these paths begin in user [IMG]http://forums.codeblocks.org/Smileys/classic/huh.gif[/IMG][IMG]http://forums.codeblocks.org/Smileys/classic/huh.gif[/IMG]?

---

### Post by JoseJesus on 2012-07-19
I'm going crazy!
 this time, compiled as before,
 without the line pkg-config ...
 and have something different!
 this is what I get

 -------------- Build: Debug in gtkapi ---------------

 Compiling: gtkApi.cpp
 In file included from / usr/include/glib-2.0/glib/galloca.h: 34:0,
                  from / usr/include/glib-2.0/glib.h: 32,
                  from / usr/include/glib-2.0/gobject/gbinding.h: 30,
                  from / usr/include/glib-2.0/glib-object.h: 25,
                  from / usr/include/glib-2.0/gio/gioenums.h: 30,
                  from / usr/include/glib-2.0/gio/giotypes.h: 30,
                  from / usr/include/glib-2.0/gio/gio.h: 28,
                  from / usr/include/gtk-2.0/gdk/gdkapplaunchcontext.h: 30,
                  from / usr/include/gtk-2.0/gdk/gdk.h: 32,
                  from / usr/include/gtk-2.0/gtk/gtk.h: 32,
                  from / home / jose / Documents / program / GTK / gtkapi / gtkApi.cpp: 7:
 / usr/include/glib-2.0/glib/gtypes.h: 34:24: Fatal error: glibconfig.h: File or directory does not exist
 finished building.
 Process terminated with status 1 (0 minutes, 0 seconds)
 1 errors, 0 warnings

looks better, but now the problem is not in eata <glibconfig.h> and I have not found. Do some more missing pak?

---

### Post by JoseJesus on 2012-07-19
My apologies, but I'm talking to myself.
 something strange is happening with CodeBlocks, because now I copy / paste and have it seem like work.
 This time the build progressed, but do not understand this error



static void fileopen_activated (GtkMenuItem *fileopen, GtkWindow *parentWindow)
{
 error L68-->>   MessageBox(parentWindow, "Menu fileopen was clicked.");
}

  / home / jose / Documents / program / GTK / gtkapi / gtkApi.cpp | 46 | warning: format not a string literal format and the arguments [-Wformat-security] |
 / home / jose / Documents / program / GTK / gtkapi / gtkApi.cpp | 68 | warning: deprecated conversion from string constant to 'char *' [-Wwrite-strings] |


 | | === Build finished: 14 errors, 0 warnings === |

---

