---
title: "Trying to compile a blank window with GTK3"
date: 2014-05-03
forum: Packaging and Compiling Programs
---

### Post by billybobjoe997 on 2014-05-03
Hello everyone,

I want to learn how to code GUI programs in Linux, so I chose GTK3, but I'm running into some issues compiling the code for a simple blank window in GTK3. I'm using the Code::Blocks IDE, and this is my code. I'm almost certain it's correct because I copy-and-pasted it from a well known GTK tutorial site. Anyway, here's the code I have:

```
#include <gtk-3.0/gtk/gtk.h>

int main( int argc, char *argv[])
{
  GtkWidget *window;


  gtk_init(&argc, &argv);


  window = gtk_window_new(GTK_WINDOW_TOPLEVEL);
  gtk_widget_show(window);


  gtk_main();


  return 0;
}
```

The code can't compile, and Code::Blocks states: "fatal error: gdk/gdk.h: No such file or directory"

I don't know why it says this, because I can look in my usr/include folder and I see the gdk folder as well as gdk.h within it. Before I tried to compile the code I installed GTK 3.0+ via the following console command:
```
[FONT=Ubuntu Mono]sudo apt-get install libgtk-3-dev[/FONT]
```

What am I doing wrong? I would greatly appreciate any help you guys can give me. :)

---

### Post by billybobjoe997 on 2014-05-03
OK, quick update and I feel dumb, haha. I looked in my include directory and I do not see a gdk folder. The problem must be that I don't have GDK installed. How do I install it? Sorry, I'm a linux newbie.

---

### Post by steeldriver on 2014-05-03
Can you compile it manually (i.e. on the command line) e.g. using something like

```

gcc -o window-gtk3 window-gtk3.c `pkg-config --cflags --libs gtk+-3.0`

```

If so, it's just a matter of specifying the equivalent headers and libraries within the Code::Blocks IDE - I'm not sure if you can do that directly using pkg-config, if not you can run

```

pkg-config --cflags gtk+-3.0

pkg-config --libs gtk+-3.0

```

and copy the results into the appropriate place in the IDE.

---

### Post by billybobjoe997 on 2014-05-03
This is what I get after running pkg-config --cflags gtk+-3.0

```
-pthread -I/usr/include/gtk-3.0 -I/usr/include/atk-1.0 -I/usr/include/at-spi2-atk/2.0 -I/usr/include/pango-1.0 -I/usr/include/gio-unix-2.0/ -I/usr/include/cairo -I/usr/include/gdk-pixbuf-2.0 -I/usr/include/glib-2.0 -I/usr/lib/i386-linux-gnu/glib-2.0/include -I/usr/include/harfbuzz -I/usr/include/freetype2 -I/usr/include/pixman-1 -I/usr/include/libpng12
```

And this is what I get after running pkg-config --libs gtk+-3.0

```
-lgtk-3 -lgdk-3 -latk-1.0 -lgio-2.0 -lpangocairo-1.0 -lgdk_pixbuf-2.0 -lcairo-gobject -lpango-1.0 -lcairo -lgobject-2.0 -lglib-2.0 
```

This basically states the package dependencies that GTK3+ uses, correct? So I need to put this information in Code::Blocks to tell it where the dependencies are? I'm not sure how to do this, again, I'm new to Code::Blocks and Linux (I'm not a hugely experienced coder, and my current knowledge comes from working with Visual Studio on Windows)

---

### Post by steeldriver on 2014-05-03
You would likely need to add each include path (-I/.../.../) to the Build Options --> Compiler --> Search directories, and each library and library path to the Build Options --> Linker Settings. I seem to remember reading something about a plug-in to allow direct use of pkg-config but that may have been for a different IDE - I'm actually quite a fan of Visual Studio, but on *nix I usually find it's easier to use a commandline / makefile approach.

The required GDK components should have been installed as dependencies of libgtk-3-dev - I was able to build and run the code from your post just using the command line as per my previous post.

---

### Post by billybobjoe997 on 2014-05-03
I tried to compile the program using the command line, with the commands you said above. First, I cded to the folder in which my .cpp file was in. Then I entered the following command:

gcc -o main main.cpp 'pkg-config --cflags --libs gtk+-3.0'

and it said: gcc: error: pkg-config --cflags --libs gtk+-3.0: No such file or directory.

---

### Post by steeldriver on 2014-05-03
You need to use the exact punctuation I posted (backticks ` ... ` not regular single quotes ' ... ') to get the intended command expansion. Alternatively you can use $( ... )

```

gcc -o main main.cpp $(pkg-config --cflags --libs gtk+-3.0)

```

The $(...) is actually preferred in general use - but the older backtick form is more makefile-friendly.

---

### Post by billybobjoe997 on 2014-05-03
Hooray! I got it to work! Thanks so much steeldriver, you are awesome. I was able to get it to compile through the console. I still could use some help though on how to get it working in code blocks. As a last resort though, I guess I can always use the console to compile it.

---

### Post by billybobjoe997 on 2014-05-03
Ah, I actually figured out how to compile it in Code::Blocks. The solution was simple. I went to the Settings -> Compile menu, and in the 'Global compiler settings' section, I clicked the 'Other options' tab, and added 
[COLOR=#000000][FONT=Ubuntu Mono]
```
$(pkg-config --cflags --libs gtk+-3.0)
```

[/FONT][/COLOR]Everything compiled wonderfully after that in Code::Blocks. Time to start learning GTK3+ now.[COLOR=#000000][FONT=Ubuntu Mono]

[/FONT][/COLOR]

---

### Post by steeldriver on 2014-05-03
That's good to know! thanks for posting back

---

