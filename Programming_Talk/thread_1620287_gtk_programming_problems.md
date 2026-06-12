---
title: "gtk programming problems"
date: 2010-11-12
forum: Programming Talk
---

### Post by solaris235 on 2010-11-12
[B]Hi all, I'm trying to do some programming with GTK.
I have everything installed libs and includes and GTK applications run fine.
But trying to compile this simple program...
[/B]
#include <gtk/gtk.h>

int main( int argc, char *argv[])
{
  GtkWidget *window;

  gtk_init(&argc, &argv);

  window = gtk_window_new(GTK_WINDOW_TOPLEVEL);
  gtk_widget_show(window);

  gtk_main();

  return 0;
}

**I get a whole bunch of errors.**


make all 
Building file: ../Test.cpp
Invoking: GCC C++ Compiler
g++ -I/usr/include/gtk-2.0 -I/usr/include/glib-2.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/lib/gtk-2.0/include -I/usr/include/gdk-pixbuf-2.0 -I/usr/include/atk-1.0 -O0 -g3 -Wall -c -fmessage-length=0 -MMD -MP -MF"Test.d" -MT"Test.d" -o"Test.o" "../Test.cpp"
In file included from /usr/include/glib-2.0/glib/gtypes.h:35,
                 from /usr/include/glib-2.0/glib/galloca.h:34,
                 from /usr/include/glib-2.0/glib.h:32,
                 from /usr/include/glib-2.0/gobject/gbinding.h:30,
                 from /usr/include/glib-2.0/glib-object.h:25,
                 from /usr/include/glib-2.0/gio/gioenums.h:30,
                 from /usr/include/glib-2.0/gio/giotypes.h:30,
                 from /usr/include/glib-2.0/gio/gio.h:28,
                 from /usr/include/gtk-2.0/gdk/gdkapplaunchcontext.h:30,
                 from /usr/include/gtk-2.0/gdk/gdk.h:32,
                 from /usr/include/gtk-2.0/gtk/gtk.h:32,
                 from ../Test.cpp:8:
/usr/include/glib-2.0/glib/gmacros.h:47: warning: "G_GNUC_EXTENSION" redefined
/usr/include/glib-2.0/glibconfig.h:38: note: this is the location of the previous definition
In file included from /usr/include/glib-2.0/glib/gasyncqueue.h:34,
                 from /usr/include/glib-2.0/glib.h:34,
                 from /usr/include/glib-2.0/gobject/gbinding.h:30,
                 from /usr/include/glib-2.0/glib-object.h:25,
                 from /usr/include/glib-2.0/gio/gioenums.h:30,
                 from /usr/include/glib-2.0/gio/giotypes.h:30,
                 from /usr/include/glib-2.0/gio/gio.h:28,
                 from /usr/include/gtk-2.0/gdk/gdkapplaunchcontext.h:30,
                 from /usr/include/gtk-2.0/gdk/gdk.h:32,
                 from /usr/include/gtk-2.0/gtk/gtk.h:32,
                 from ../Test.cpp:8:
/usr/include/glib-2.0/glib/gthread.h:271: error: ‘GSystemThread’ does not name a type
In file included from /usr/include/glib-2.0/glib/giochannel.h:35,
                 from /usr/include/glib-2.0/glib.h:53,
                 from /usr/include/glib-2.0/gobject/gbinding.h:30,
                 from /usr/include/glib-2.0/glib-object.h:25,
                 from /usr/include/glib-2.0/gio/gioenums.h:30,
                 from /usr/include/glib-2.0/gio/giotypes.h:30,
                 from /usr/include/glib-2.0/gio/gio.h:28,
                 from /usr/include/gtk-2.0/gdk/gdkapplaunchcontext.h:30,
                 from /usr/include/gtk-2.0/gdk/gdk.h:32,
                 from /usr/include/gtk-2.0/gtk/gtk.h:32,
                 from ../Test.cpp:8:
/usr/include/glib-2.0/glib/gmain.h:136: error: typedef ‘GChildWatchFunc’ is initialized (use decltype instead)
/usr/include/glib-2.0/glib/gmain.h:136: error: ‘GPid’ was not declared in this scope
/usr/include/glib-2.0/glib/gmain.h:137: error: expected primary-expression before ‘status’
/usr/include/glib-2.0/glib/gmain.h:138: error: expected primary-expression before ‘data’
/usr/include/glib-2.0/glib/gmain.h:376: error: ‘GPid’ was not declared in this scope
/usr/include/glib-2.0/glib/gmain.h:509: error: ‘GPid’ has not been declared
/usr/include/glib-2.0/glib/gmain.h:510: error: ‘GChildWatchFunc’ has not been declared
/usr/include/glib-2.0/glib/gmain.h:513: error: ‘GPid’ was not declared in this scope
/usr/include/glib-2.0/glib/gmain.h:514: error: ‘GChildWatchFunc’ was not declared in this scope
/usr/include/glib-2.0/glib/gmain.h:515: error: expected primary-expression before ‘data’
/usr/include/glib-2.0/glib/gmain.h:515: error: initializer expression list treated as compound expression
In file included from /usr/include/glib-2.0/glib.h:61,
                 from /usr/include/glib-2.0/gobject/gbinding.h:30,
                 from /usr/include/glib-2.0/glib-object.h:25,
                 from /usr/include/glib-2.0/gio/gioenums.h:30,
                 from /usr/include/glib-2.0/gio/giotypes.h:30,
                 from /usr/include/glib-2.0/gio/gio.h:28,
                 from /usr/include/gtk-2.0/gdk/gdkapplaunchcontext.h:30,
                 from /usr/include/gtk-2.0/gdk/gdk.h:32,
                 from /usr/include/gtk-2.0/gtk/gtk.h:32,
                 from ../Test.cpp:8:
/usr/include/glib-2.0/glib/gmessages.h:110: error: expected constructor, destructor, or type conversion before ‘void’
In file included from /usr/include/glib-2.0/glib.h:78,
                 from /usr/include/glib-2.0/gobject/gbinding.h:30,
                 from /usr/include/glib-2.0/glib-object.h:25,
                 from /usr/include/glib-2.0/gio/gioenums.h:30,
                 from /usr/include/glib-2.0/gio/giotypes.h:30,
                 from /usr/include/glib-2.0/gio/gio.h:28,
                 from /usr/include/gtk-2.0/gdk/gdkapplaunchcontext.h:30,
                 from /usr/include/gtk-2.0/gdk/gdk.h:32,
                 from /usr/include/gtk-2.0/gtk/gtk.h:32,
                 from ../Test.cpp:8:
/usr/include/glib-2.0/glib/gspawn.h:92: error: ‘GPid’ has not been declared
/usr/include/glib-2.0/glib/gspawn.h:105: error: ‘GPid’ has not been declared
/usr/include/glib-2.0/glib/gspawn.h:135: error: variable or field ‘g_spawn_close_pid’ declared void
/usr/include/glib-2.0/glib/gspawn.h:135: error: ‘GPid’ was not declared in this scope
In file included from /usr/include/glib-2.0/gobject/gobject.h:26,
                 from /usr/include/glib-2.0/gobject/gbinding.h:31,
                 from /usr/include/glib-2.0/glib-object.h:25,
                 from /usr/include/glib-2.0/gio/gioenums.h:30,
                 from /usr/include/glib-2.0/gio/giotypes.h:30,
                 from /usr/include/glib-2.0/gio/gio.h:28,
                 from /usr/include/gtk-2.0/gdk/gdkapplaunchcontext.h:30,
                 from /usr/include/gtk-2.0/gdk/gdk.h:32,
                 from /usr/include/gtk-2.0/gtk/gtk.h:32,
                 from ../Test.cpp:8:
/usr/include/glib-2.0/gobject/gtype.h:1665: error: expected constructor, destructor, or type conversion before ‘void’
/usr/include/glib-2.0/gobject/gtype.h:1666: error: expected constructor, destructor, or type conversion before ‘void’
/usr/include/glib-2.0/gobject/gtype.h:1667: error: expected constructor, destructor, or type conversion before ‘void’
/usr/include/glib-2.0/gobject/gtype.h:1668: error: expected constructor, destructor, or type conversion before ‘void’
/usr/include/glib-2.0/gobject/gtype.h:1669: error: expected constructor, destructor, or type conversion before ‘void’
/usr/include/glib-2.0/gobject/gtype.h:1670: error: expected constructor, destructor, or type conversion before ‘void’
/usr/include/glib-2.0/gobject/gtype.h:1671: error: expected constructor, destructor, or type conversion before ‘void’
/usr/include/glib-2.0/gobject/gtype.h:1672: error: expected constructor, destructor, or type conversion before ‘void’
/usr/include/glib-2.0/gobject/gtype.h:1673: error: expected constructor, destructor, or type conversion before ‘void’
In file included from /usr/include/glib-2.0/gio/giotypes.h:30,
                 from /usr/include/glib-2.0/gio/gio.h:28,
                 from /usr/include/gtk-2.0/gdk/gdkapplaunchcontext.h:30,
                 from /usr/include/gtk-2.0/gdk/gdk.h:32,
                 from /usr/include/gtk-2.0/gtk/gtk.h:32,
                 from ../Test.cpp:8:
/usr/include/glib-2.0/gio/gioenums.h:630: error: ‘GLIB_SYSDEF_AF_INET’ was not declared in this scope
/usr/include/glib-2.0/gio/gioenums.h:631: error: ‘GLIB_SYSDEF_AF_INET6’ was not declared in this scope
/usr/include/glib-2.0/gio/gioenums.h:676: error: ‘GLIB_SYSDEF_MSG_OOB’ was not declared in this scope
/usr/include/glib-2.0/gio/gioenums.h:677: error: ‘GLIB_SYSDEF_MSG_PEEK’ was not declared in this scope
/usr/include/glib-2.0/gio/gioenums.h:678: error: ‘GLIB_SYSDEF_MSG_DONTROUTE’ was not declared in this scope
/usr/include/glib-2.0/glib/gutils.h:301: warning: ‘gint g_bit_nth_lsf(gulong, gint)’ declared ‘static’ but never defined
/usr/include/glib-2.0/glib/gutils.h:303: warning: ‘gint g_bit_nth_msf(gulong, gint)’ declared ‘static’ but never defined
/usr/include/glib-2.0/glib/gutils.h:305: warning: ‘guint g_bit_storage(gulong)’ declared ‘static’ but never defined
/usr/include/glib-2.0/glib/gutils.h:316: warning: ‘void g_trash_stack_push(GTrashStack**, void*)’ declared ‘static’ but never defined
/usr/include/glib-2.0/glib/gutils.h:318: warning: ‘void* g_trash_stack_pop(GTrashStack**)’ declared ‘static’ but never defined
/usr/include/glib-2.0/glib/gutils.h:319: warning: ‘void* g_trash_stack_peek(GTrashStack**)’ declared ‘static’ but never defined
/usr/include/glib-2.0/glib/gutils.h:320: warning: ‘guint g_trash_stack_height(GTrashStack**)’ declared ‘static’ but never defined
/usr/include/glib-2.0/glib/gthread.h:339: warning: ‘gboolean g_once_init_enter(volatile gsize*)’ declared ‘static’ but never defined
make: *** [Test.o] Error 1



[B]There were some more but I discovered some declarations in various include files that were commented out. I removed the comments and some of those errors were gone.
I'm thinking I have the wrong development package. I'm using the package that installed with Ubuntu 10.10

I've also compared header files with these packages
gtk+-2.22.0
pango-1.28.3
glib-2.26.0
I can't find any differences
Anybody have any ideas ??????

[/B]

---

### Post by Kcj1993 on 2010-11-13
[http://library.gnome.org/devel/gtk/2.21/gtk-compiling.html](http://library.gnome.org/devel/gtk/2.21/gtk-compiling.html)

---

### Post by solaris235 on 2010-11-13
Thanks, but I've been there and done that.
The compiler finds all the files it's looking for.
The linker finds all the files it's looking for.
There are definite problems with the set of development files that I have.
I've tried Eclipse, Netbeans, Codelite, and direct from the command line with the files explicitly entered and with the pkg-config with the same result every time.
Even compiling the assembler version of the same code yields the same results.
I'm getting quite frustrated.

---

### Post by nvteighen on 2010-11-14
Let's see...

0. You say you installed GTK+... From where? How? You know the best way to do it is by installing the libgtk2.0-dev package... This may seem obvious, but sometimes people that use KDE fear that doing that will install the whole GNOME suite (which won't happen) and try installing GTK+ from source.

1. You're using a really weird compiling command. The way to compile GTK+ applications is the following:

```

# Using gcc... see below
gcc -o my_app my_app.c -Wall -Wextra -pedantic $(pkg-config --cflags --libs gtk+-2.0)

```

I see you're using a Makefile. Please, post it... the bug is surely there.

2. Use gcc and g++ properly. Your code, despite having the *.cpp extension is C, not C++... and GTK+ is C (gtkmm is C++). Ok, this may sound a bit snobbish or whatever, but it's always better to use the corresponding compiler... or you may get some quirks. It wouldn't be the first time we come across some error produced by trying to compile C code with g++ (no, C++ isn't a strict superset of C... and moreover, it changes some fundamental parts of C semantics). I compiled your code using g++ and I got no errors. Also, if you're going for C++ GTK+ programming, I highly recommend you to use gtkmm instead... gtkmm will make use of all OOP features C++ has and make everything much easier for you.

---

### Post by solaris235 on 2010-11-14
Hey [nvteighen]("http://ubuntuforums.org/member.php?u=273037"), thanks for the response and the things to try.

0. I'm using Ubuntu 10.10 with the gnome desktop, GTK+ is install with the system. I did install the  libgtk2.0-dev package through the package manager.

1.The compile command I used is generated by Eclipse, I also tried yours and I get the same errors only worded for C instead of C++

Here's the Eclipse generated make file

################################################################################
# Automatically-generated file. Do not edit!
################################################################################

-include ../makefile.init

RM := rm -rf

# All of the sources participating in the build are defined here
-include sources.mk
-include subdir.mk
-include objects.mk

ifneq ($(MAKECMDGOALS),clean)
ifneq ($(strip $(C++_DEPS)),)
-include $(C++_DEPS)
endif
ifneq ($(strip $(C_DEPS)),)
-include $(C_DEPS)
endif
ifneq ($(strip $(CC_DEPS)),)
-include $(CC_DEPS)
endif
ifneq ($(strip $(CPP_DEPS)),)
-include $(CPP_DEPS)
endif
ifneq ($(strip $(CXX_DEPS)),)
-include $(CXX_DEPS)
endif
ifneq ($(strip $(C_UPPER_DEPS)),)
-include $(C_UPPER_DEPS)
endif
endif

-include ../makefile.defs

# Add inputs and outputs from these tool invocations to the build variables 

# All Target
all: Test

# Tool invocations
Test: $(OBJS) $(USER_OBJS)
    @echo 'Building target: $@'
    @echo 'Invoking: GCC C++ Linker'
    g++ -L/usr/lib -L/lib -o"Test" $(OBJS) $(USER_OBJS) $(LIBS)
    @echo 'Finished building target: $@'
    @echo ' '

# Other Targets
clean:
    -$(RM) $(OBJS)$(C++_DEPS)$(C_DEPS)$(CC_DEPS)$(CPP_DEPS)$(EXECUTABLES)$(CXX_DEPS)$(C_UPPER_DEPS) Test
    -@echo ' '

.PHONY: all clean dependents
.SECONDARY:

-include ../makefile.targets

2. I know that the code should compile and run because everyone else can get it to work but me. I've tried gcc and g++. Ultimately I want to do my coding in assembler which should work fine using gcc and gtk. I'm just trying to get gtk development package working. 

I guess I can always just use X11 directly. (but I don't wanna)

Any more idea's....  anyone....

---

### Post by nvteighen on 2010-11-14
> **solaris235 said:**
> 
1.The compile command I used is generated by Eclipse, I also tried yours and I get the same errors only worded for C instead of C++


Wait a minute. Did you use my command on Eclipse?

Ugh... I see I didn't mention you to use it on a Terminal, rather than on the IDE. I haven't ever used Eclipse, so I don't know how it is supposed to work; what I want you to check is whether it is an IDE-related thing or something else is preventing the code to compile (I'm able to compile it and I can assure you your code is correct except for a detail that's irrelevant now).

So, please, enter the compile command I posted before into a Terminal.

---

### Post by solaris235 on 2010-11-14
[B]I did run your command line in a terminal. Like I said earlier I've tried this with 3 different IDE's as well as the terminal.

I've since done a full reinstall of glib, pango, atk, gtk+ as directed on the GTK+ website. Everything went perfectly.
BUT...
My error count has dropped to 25 errors[/B]   
[B]So I'm making progress...
But it still doesn't work!!!!! arg!!!
I must still be missing an include file or there is a declare statement missing somewhere.

[/B]**** Build of configuration Debug for project TestC ****

make all 
Building file: ../Test.c
Invoking: GCC C Compiler
gcc -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/gdk-pixbuf-2.0 -O0 -g3 -Wall -c -fmessage-length=0 -MMD -MP -MF"Test.d" -MT"Test.d" -o"Test.o" "../Test.c"
In file included from /usr/include/glib-2.0/glib/gtypes.h:35,
                 from /usr/include/glib-2.0/glib/galloca.h:34,
                 from /usr/include/glib-2.0/glib.h:32,
                 from /usr/include/glib-2.0/gobject/gbinding.h:30,
                 from /usr/include/glib-2.0/glib-object.h:25,
                 from /usr/include/glib-2.0/gio/gioenums.h:30,
                 from /usr/include/glib-2.0/gio/giotypes.h:30,
                 from /usr/include/glib-2.0/gio/gio.h:28,
                 from /usr/include/gtk-2.0/gdk/gdkapplaunchcontext.h:30,
                 from /usr/include/gtk-2.0/gdk/gdk.h:32,
                 from /usr/include/gtk-2.0/gtk/gtk.h:32,
                 from ../Test.c:8:
/usr/include/glib-2.0/glib/gmacros.h:47: warning: "G_GNUC_EXTENSION" redefined
/usr/include/glib-2.0/glibconfig.h:38: note: this is the location of the previous definition
In file included from /usr/include/glib-2.0/glib/gasyncqueue.h:34,
                 from /usr/include/glib-2.0/glib.h:34,
                 from /usr/include/glib-2.0/gobject/gbinding.h:30,
                 from /usr/include/glib-2.0/glib-object.h:25,
                 from /usr/include/glib-2.0/gio/gioenums.h:30,
                 from /usr/include/glib-2.0/gio/giotypes.h:30,
                 from /usr/include/glib-2.0/gio/gio.h:28,
                 from /usr/include/gtk-2.0/gdk/gdkapplaunchcontext.h:30,
                 from /usr/include/gtk-2.0/gdk/gdk.h:32,
                 from /usr/include/gtk-2.0/gtk/gtk.h:32,
                 from ../Test.c:8:
/usr/include/glib-2.0/glib/gthread.h:271: error: expected specifier-qualifier-list before &#8216;GSystemThread&#8217;
In file included from /usr/include/glib-2.0/glib/giochannel.h:35,
                 from /usr/include/glib-2.0/glib.h:53,
                 from /usr/include/glib-2.0/gobject/gbinding.h:30,
                 from /usr/include/glib-2.0/glib-object.h:25,
                 from /usr/include/glib-2.0/gio/gioenums.h:30,
                 from /usr/include/glib-2.0/gio/giotypes.h:30,
                 from /usr/include/glib-2.0/gio/gio.h:28,
                 from /usr/include/gtk-2.0/gdk/gdkapplaunchcontext.h:30,
                 from /usr/include/gtk-2.0/gdk/gdk.h:32,
                 from /usr/include/gtk-2.0/gtk/gtk.h:32,
                 from ../Test.c:8:
/usr/include/glib-2.0/glib/gmain.h:136: error: expected &#8216;)&#8217; before &#8216;pid&#8217;
/usr/include/glib-2.0/glib/gmain.h:376: error: expected &#8216;)&#8217; before &#8216;pid&#8217;
/usr/include/glib-2.0/glib/gmain.h:509: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;GPid&#8217;
/usr/include/glib-2.0/glib/gmain.h:510: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;GChildWatchFunc&#8217;
/usr/include/glib-2.0/glib/gmain.h:513: error: expected &#8216;)&#8217; before &#8216;pid&#8217;
In file included from /usr/include/glib-2.0/glib.h:61,
                 from /usr/include/glib-2.0/gobject/gbinding.h:30,
                 from /usr/include/glib-2.0/glib-object.h:25,
                 from /usr/include/glib-2.0/gio/gioenums.h:30,
                 from /usr/include/glib-2.0/gio/giotypes.h:30,
                 from /usr/include/glib-2.0/gio/gio.h:28,
                 from /usr/include/gtk-2.0/gdk/gdkapplaunchcontext.h:30,
                 from /usr/include/gtk-2.0/gdk/gdk.h:32,
                 from /usr/include/gtk-2.0/gtk/gtk.h:32,
                 from ../Test.c:8:
/usr/include/glib-2.0/glib/gmessages.h:110: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;void&#8217;
In file included from /usr/include/glib-2.0/glib.h:78,
                 from /usr/include/glib-2.0/gobject/gbinding.h:30,
                 from /usr/include/glib-2.0/glib-object.h:25,
                 from /usr/include/glib-2.0/gio/gioenums.h:30,
                 from /usr/include/glib-2.0/gio/giotypes.h:30,
                 from /usr/include/glib-2.0/gio/gio.h:28,
                 from /usr/include/gtk-2.0/gdk/gdkapplaunchcontext.h:30,
                 from /usr/include/gtk-2.0/gdk/gdk.h:32,
                 from /usr/include/gtk-2.0/gtk/gtk.h:32,
                 from ../Test.c:8:
/usr/include/glib-2.0/glib/gspawn.h:92: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;GPid&#8217;
/usr/include/glib-2.0/glib/gspawn.h:105: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;GPid&#8217;
/usr/include/glib-2.0/glib/gspawn.h:135: error: expected &#8216;)&#8217; before &#8216;pid&#8217;
In file included from /usr/include/glib-2.0/gobject/gobject.h:26,
                 from /usr/include/glib-2.0/gobject/gbinding.h:31,
                 from /usr/include/glib-2.0/glib-object.h:25,
                 from /usr/include/glib-2.0/gio/gioenums.h:30,
                 from /usr/include/glib-2.0/gio/giotypes.h:30,
                 from /usr/include/glib-2.0/gio/gio.h:28,
                 from /usr/include/gtk-2.0/gdk/gdkapplaunchcontext.h:30,
                 from /usr/include/gtk-2.0/gdk/gdk.h:32,
                 from /usr/include/gtk-2.0/gtk/gtk.h:32,
                 from ../Test.c:8:
/usr/include/glib-2.0/gobject/gtype.h:1665: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;void&#8217;
/usr/include/glib-2.0/gobject/gtype.h:1666: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;void&#8217;
/usr/include/glib-2.0/gobject/gtype.h:1667: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;void&#8217;
/usr/include/glib-2.0/gobject/gtype.h:1668: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;void&#8217;
/usr/include/glib-2.0/gobject/gtype.h:1669: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;void&#8217;
/usr/include/glib-2.0/gobject/gtype.h:1670: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;void&#8217;
/usr/include/glib-2.0/gobject/gtype.h:1671: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;void&#8217;
/usr/include/glib-2.0/gobject/gtype.h:1672: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;void&#8217;
/usr/include/glib-2.0/gobject/gtype.h:1673: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;void&#8217;
In file included from /usr/include/glib-2.0/gio/giotypes.h:30,
                 from /usr/include/glib-2.0/gio/gio.h:28,
                 from /usr/include/gtk-2.0/gdk/gdkapplaunchcontext.h:30,
                 from /usr/include/gtk-2.0/gdk/gdk.h:32,
                 from /usr/include/gtk-2.0/gtk/gtk.h:32,
                 from ../Test.c:8:
/usr/include/glib-2.0/gio/gioenums.h:630: error: &#8216;GLIB_SYSDEF_AF_INET&#8217; undeclared here (not in a function)
/usr/include/glib-2.0/gio/gioenums.h:631: error: &#8216;GLIB_SYSDEF_AF_INET6&#8217; undeclared here (not in a function)
/usr/include/glib-2.0/gio/gioenums.h:676: error: &#8216;GLIB_SYSDEF_MSG_OOB&#8217; undeclared here (not in a function)
/usr/include/glib-2.0/gio/gioenums.h:677: error: &#8216;GLIB_SYSDEF_MSG_PEEK&#8217; undeclared here (not in a function)
/usr/include/glib-2.0/gio/gioenums.h:678: error: &#8216;GLIB_SYSDEF_MSG_DONTROUTE&#8217; undeclared here (not in a function)
make: *** [Test.o] Error 1

---

### Post by gmargo on 2010-11-14
Your code compiles fine for for me on 10.10 Maverick, written as a C file.  The only additions needed were the appropriate **pkg-config** commands to set CFLAGS and LDFLAGS properly.  As with the following makefile:
```

CC=gcc
CFLAGS=-Wall -O0 -g3
CFLAGS+=$(shell  pkg-config --cflags gtk+-2.0)
LDFLAGS+=$(shell pkg-config --libs   gtk+-2.0)

hello_gtk1: hello_gtk1.c
        $(CC) $(CFLAGS) $(LDFLAGS) -o hello_gtk1 hello_gtk1.c


```What version gcc are you using?
```

$ gcc --version
gcc-4.4.real (Ubuntu/Linaro 4.4.4-14ubuntu5) 4.4.5

```Here's how the make expanded (without CODE blocking so the line wraps):

gcc -Wall -O0 -g3 -pthread -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/gdk-pixbuf-2.0 -I/usr/include/pango-1.0 -I/usr/include/gio-unix-2.0/ -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/libpng12   -pthread -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lgio-2.0 -lpangoft2-1.0 -lpangocairo-1.0 -lgdk_pixbuf-2.0 -lm -lcairo -lpng12 -lpango-1.0 -lfreetype -lfontconfig -lgobject-2.0 -lgmodule-2.0 -lgthread-2.0 -lrt -lglib-2.0   -o hello_gtk1 hello_gtk1.c

---

### Post by solaris235 on 2010-11-14
Hey gmargo, thanks for the input...
I'm using...

```
gcc (Ubuntu/Linaro 4.4.4-14ubuntu5) 4.4.5
Copyright (C) 2010 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.
```I've used pkg-config in every way that it can be used,
I tried your makefile,
I tried your gcc command line,
I still get the same errors.


I know the C code it good. (everyone else can get it to compile and run)
I know that gtk+ runs on my Maverick system. (Other apps that use gtk+ work fine)
I know that gcc works fine.(I can compile and run other programs that don't use gtk)
I know that g++ works fine.(for the same reason as gcc works)

That leaves my development package as the problem
Here are the libgtk2.0 packages that I have installed

libgtk2.0-0
libgtk2.0-doc
libgtk2.0-0-dbg
libgtk2.0-common
libgtk2.0-bin
libgtk2.0-dev
libgtk2.0-cil

installed versions of everything are 2.22.0-0ubuntu1 except libgtk2.0-cil ver: 2.10.12-1
in case it matters I have Gimp Version 2.6.11-1~getdeb1~maverick installed as well.

am I missing something or should I remove something ??????

---

### Post by gmargo on 2010-11-15
> **solaris235 said:**
> 
make all 
Building file: ../Test.c
Invoking: GCC C Compiler
gcc -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/gdk-pixbuf-2.0 -O0 -g3 -Wall -c -fmessage-length=0 -MMD -MP -MF"Test.d" -MT"Test.d" -o"Test.o" "../Test.c"
In file included from /usr/include/glib-2.0/glib/gtypes.h:35,
                 from /usr/include/glib-2.0/glib/galloca.h:34,
                 from /usr/include/glib-2.0/glib.h:32,
                 from /usr/include/glib-2.0/gobject/gbinding.h:30,
                 from /usr/include/glib-2.0/glib-object.h:25,
                 from /usr/include/glib-2.0/gio/gioenums.h:30,
                 from /usr/include/glib-2.0/gio/giotypes.h:30,
                 from /usr/include/glib-2.0/gio/gio.h:28,
                 from /usr/include/gtk-2.0/gdk/gdkapplaunchcontext.h:30,
                 from /usr/include/gtk-2.0/gdk/gdk.h:32,
                 from /usr/include/gtk-2.0/gtk/gtk.h:32,
                 from ../Test.c:8:
**/usr/include/glib-2.0/glib/gmacros.h**:47: warning: "G_GNUC_EXTENSION" redefined
**/usr/include/glib-2.0/glibconfig.h**:38: note: this is the location of the previous definition


I find this error message very interesting.

I do not have this file: **/usr/include/glib-2.0/glibconfig.h**. "locate glibconfig.h" on my system shows it at this path: _/usr/lib/glib-2.0/include/glibconfig.h_, and it does not contain the G_GNUC_EXTENSION definition.  It is from the [libglib2.0-dev]("http://packages.ubuntu.com/maverick/libglib2.0-dev") package.

So where did that file come from?  Try "dpkg -S  /usr/include/glib-2.0/glibconfig.h".  And take a look at it.  Is it a symbolic link? Or a misnamed copy of something else?

---

### Post by Vox754 on 2010-11-15
> **solaris235 said:**
> ...
I know that gtk+ runs on my Maverick system. (Other apps that use gtk+ work fine)
...


That you are using the GNOME desktop and all Gtk+ applications are running fine, means nothing when it comes to compiling from source. Compilation is different from just running the programs.

Programs such as gedit, gnome-terminal, etc. do not use the Gtk+ development files (C or C++ headers) at all when they run. So, you cannot say you have development files installed correctly just by watching at other programs.

> ...
installed versions of everything are 2.22.0-0ubuntu1 except libgtk2.0-cil ver: 2.10.12-1
in case it matters I have Gimp Version 2.6.11-1~getdeb1~maverick installed as well.

am I missing something or should I remove something ??????

It is obvious that there is something wrong installed on your system. But it's hard to tell exactly what because you have not given enough information. Removed symlinks, created directories, removed files, copied directories, commented lines of code, installed new compiler, added software sources, added other repositories, changed PATH, LD_LIBRARY_PATH, or other variables? You need to be more precise.

You mentioned earlier: "I've since done a full reinstall of glib, pango, atk, gtk+ as directed on the GTK+ website."

This is probably your error, that you manually tried to install stuff, and now your system is in an unstable state. In the future, use the package manager to install important development files, unless you really know what you are doing.

At this point, I would suggest you to reinstall Ubuntu 10.10, and then try to install the development files again, through the package manager.

Also, post code in this forum using "code" tags, otherwise it becomes difficult to read your output.

Like this:
```

Some pretty code in here in monospace font.

```

Do not compile in the IDE and do not post the automatically generated Makefile, that is useless. You need to compile through the command line, using "pkg-config", and then you know you'll be able to use an IDE.

---

### Post by nvteighen on 2010-11-16
> **Vox754 said:**
> 
Do not compile in the IDE and do not post the automatically generated Makefile, that is useless. You need to compile through the command line, using "pkg-config", and then you know you'll be able to use an IDE.

Well, I asked him to post the Makefile. I wanted to take a look at it in order to see if there was an issue there, but it seems not. But yes, I agree: it's much better to learn how the compilation process is before using an IDE because the latter actually assume you know how to configure your compiler...

@OP:
If this also fails even using the command line and you tell us you were following the install procedure on the GTK+ website, then the most probable hypothesis is that you've got two conflicting versions of GTK+.

The easiest thing to do would be to reinstall Ubuntu, but that's a pretty bad solution.

For the next time: **always** install from the repositories first; **only** install from source when the repos haven't got what you wanted. This isn't only to avoid this kind of issues, but it's also the main reason why GNU/Linux is way more secure than other OSs.

---

### Post by solaris235 on 2010-11-17
Well in the process of messing about...  
uninstalling and reinstalling various gtk related developement packages trying to find some of these missing declarations... ya you guessed it, I messed up my gdm dependancies.  

So I've now reinstalled Ubuntu 10.10 (which must be a newer build since I had lots of problems getting compiz to work. Still can't get the fusion-icon to run... but I digress)  

So now I have a clean install of the most recent Ubuntu 10.10 
Everything is installed through the software centre or package manager. (same as I did the first time ) And guess what...  

My simple app compiles links and runs just fine.  
Now I can get on with my programming.  

I'd like to thank everyone who participated in trying to help me figure this out. 

THANKS !!!!!!:guitar:

---

