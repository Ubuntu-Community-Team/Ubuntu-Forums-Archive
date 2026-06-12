---
title: "Eclipse CDT &amp; GTK setup issues"
date: 2008-06-12
forum: Programming Talk
---

### Post by pcman312 on 2008-06-12
I've never set up Eclipse CDT to use GTK before, and I'm having some issues with it. I have the following program to make sure that I've set things up right:

```
#include <gtk/gtk.h>

int main(int argc, char *argv[])
{
	GtkWidget *window;

	gtk_init(&argc, &argv);

	window = gtk_window_new(GTK_WINDOW_TOPLEVEL);
	gtk_widget_show(window);

	gtk_main();

	return 0;
}
```

However I clearly don't have it set up properly since I get errors saying that the GTK variables aren't declared in this scope and it can't find the gtk/gtk.h file. I haven't been able to figure out how to set up the project to find and recognize the GTK library. If I compile the program from the command line with:
```
g++ -o GUI GUI_Test.cpp `pkg-config --libs --cflags gtk+-2.0`
```
It compiles and runs. I'm fairly certain that adding the *`pkg-config --libs --cflags gtk+-2.0`* part to the project would fix it, however I have tried several places that seemed to make sense, but none of them have worked.

Free popcorn smilies for anyone who helps! ;)

---

### Post by xlinuks on 2008-06-12
"gtk_window_new" is for C,
you are using g++ - which is the compiler for C++.

Thus are you trying to use C or C++?

In other words you're using the source code of a C program.

---

### Post by xlinuks on 2008-06-12
For C++ try this:
```

#include <gtkmm.h>

using namespace Gtk;

int main(int argc, char *argv[])
{
  Gtk::Main kit(argc, argv);
  Window window;
  window.resize( 400, 400 );
  window.set_title( "test window" );
  window.show_all_children();
  Gtk::Main::run(window);

  return 0;
}

```

---

### Post by pcman312 on 2008-06-12
> **xlinuks said:**
> For C++ try this:
```

#include <gtkmm.h>

using namespace Gtk;

int main(int argc, char *argv[])
{
  Gtk::Main kit(argc, argv);
  Window window;
  window.resize( 400, 400 );
  window.set_title( "test window" );
  window.show_all_children();
  Gtk::Main::run(window);

  return 0;
}

```

Tried this and it's the same scenario. Can't find gtkmm.h, Gtk isn't a namespace, etc.

g++ works for c code as well since C++ is just a wrapper around C (with extra stuff of course). Any program written in C will work in C++ (with a couple of exceptions due to the new keywords in C++). The program compiles and runs fine when I compile it with g++ at the command line instead of in eclipse. I'm 99.9% sure that the problem isn't in the code, it's setting up the project in eclipse.

---

### Post by xlinuks on 2008-06-12
Uhhh sorry, I downloaded the latest Eclipse version from the web, the dedicated "C/C++" version, spent some time configuring the options of the C++ project and it still won't compile, this is pathetic! NetBeans is way easier! That's why I'm using it.

---

### Post by bruce89 on 2008-06-12
> **pcman312 said:**
> g++ works for c code as well since C++ is just a wrapper around C (with extra stuff of course). Any program written in C will work in C++ (with a couple of exceptions due to the new keywords in C++). The program compiles and runs fine when I compile it with g++ at the command line instead of in eclipse. I'm 99.9% sure that the problem isn't in the code, it's setting up the project in eclipse.

Use gcc instead of g++. There is no point in using g++ to compile C.

---

### Post by pcman312 on 2008-06-13
> **bruce89 said:**
> Use gcc instead of g++. There is no point in using g++ to compile C.

The final program will be using C++, that's why I'm using g++. The point of my question is not about the compiler, it's about the setup of the project to use the GTK libraries.

---

### Post by pcman312 on 2008-06-13
I was able to get it to work by using [this tutorial]("http://zetcode.com/articles/netbeanscdevelopment/") as a guide (although it's for netbeans, I was able to figure it out) and for posterity, here's my step by step guide for anyone else that may need it:

[LIST=1]
[*]Right click on your project and select Properties
[*]Select GCC C++ Compiler -> Directories
[*]On the right, there will be an "Include paths" area. Click on the add button and add the following directories:
[LIST]
[*]/usr/include/gtk-2.0
[*]/usr/include/atk-1.0
[*]/usr/include/cairo
[*]/usr/include/pango-1.0
[*]/usr/include/glib-2.0
[*]/usr/include/freetype2
[*]/usr/include/libpng12
[*]/usr/lib/glib-2.0/include
[*]/usr/lib/gtk-2.0/include
[/LIST]
[*]Next, select GCC C++ Linker -> Miscellaneous and add */usr/lib/libgtk-x11-2.0.so* to the Other Options (-Xlinker [option]) pane
[*]Compile and run your program
[/LIST]

---

### Post by bruce89 on 2008-06-13
> **pcman312 said:**
> The final program will be using C++, that's why I'm using g++. The point of my question is not about the compiler, it's about the setup of the project to use the GTK libraries.

You ought to use GTK-- then, it's a C++ wrapper to GTK+.

---

### Post by Agent0013 on 2009-06-15
I have tried all of the methods to set up eclipse to write a program with the GTK libraries and have gotten the program to work. But it will only compile one time. After that, if I try to build it again I get many errors of NUL characters in main.d and it does not build. If I do a project > clean, then build it again it works, but why should I have to do that extra step every time.

Again, I have tried including all of the library directories in the include paths, and the pkg-config method. They both do the same thing. 

Any help would be appreciated. I can't find any reference to a problem like this anywhere.

Error Messages:
```

**** Incremental build of configuration Release for project SlotRPS ****

make -k all 
main.d:5: warning: NUL character seen; rest of line ignored
main.d:43: warning: NUL character seen; rest of line ignored
main.d:44: warning: NUL character seen; rest of line ignored
main.d:45: warning: NUL character seen; rest of line ignored
main.d:45: *** missing separator. Stop.
Build complete for project SlotRPS

```

---

### Post by pcman312 on 2009-06-15
Which OS are you using? My setup was for a debian system, and I didn't try it for any other OS's. This could be a problem if you're using a different OS. The null character problem sounds like a problem between linux and windows since they don't handle text files quite the same.

As for the pkg-config, I didn't use it in eclipse at all, just the libraries and the linker.

---

### Post by Agent0013 on 2009-06-16
[FONT=Arial]Sorry, I didn't specify the OS. It is Kubuntu. This is a development system that I got and it had that on it. I am a little more familiar with the regular Ubuntu instalation than this one, but it is pretty similar. I am an experienced programmer and I want to start writing GUI programs on Linux. I like the look of Eclipse, but if it is too dificult to get set up I may try something else, Kdevelop perhaps. 

I have written the entire program here on this OS, so it isn't a Windows / Linux thing. I started with console only output (basic Hello World) and started adding the GUI / GTK stuff to it. If I take out the extra libraries for the GTK stuff then I don't get the errors when rebuilding. Something in those libraries seem to be causing the problem. And only when rebuilding, not if I clean the build then build it fresh. Maybe it is something with the debugging setup in Eclipse? I installed everything using the Adept package manager that is installed on this system and I have updated everthing that could be.

I also tried a simple window program using vi and compiling with 
[/FONT] [FONT=Arial]```

gcc -o simple simple.c `pkg-config --libs --cflags gtk+-2.0`

```That one had no problems no matter how many times I compiled it. So I'm not sure what part Eclipse has to do with this. I have been using the managed make project as I havn't created make files before.
[/FONT] [FONT=Arial]
Thanks for the reply and for looking at this problem.
[/FONT]

---

### Post by pcman312 on 2009-06-16
I have a feeling that the makefile that eclipse is creating for the project is slightly messed up somehow. That's why I asked about the OS dealing with the null characters. I've found that eclipse excels at writing java programs, but I haven't been impressed with it's C/C++ plugin. You could try another program that I've liked called Code::Blocks [http://www.codeblocks.org/]("http://www.codeblocks.org/"). It's specifically designed for C/C++ programming and is pretty nice. It sort of reminds me of Visual Studio, although I haven't actually used VS much. It does let you either use their own makefile that they create for a project or you can specify your own, which can potentially speed up build time and give you a bit more control over the project. It has built into it the capabilities of creating projects for different purposes including GTK, OpenGL, etc.

---

