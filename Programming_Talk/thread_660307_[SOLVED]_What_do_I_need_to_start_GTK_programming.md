---
title: "[SOLVED] What do I need to start GTK programming?"
date: 2008-01-06
forum: Programming Talk
---

### Post by rocketman768 on 2008-01-06
I read a thread that said the packages to install were: libgtk2.0-dev, libglade2-dev. I installed them and tried compiling the following program:

```

#include <gtk/gtk.h>
#include <glib.h>

gint destroyapp(GtkWidget *widget, gpointer gdata)
{
   g_print("Quitting...\n");
   gtk_main_quit();
   return FALSE;
}

void button_clicked( GtkWidget *widget, gpointer gdata )
{
   g_print("Button was clicked.\n");
}

int main( int argc, char *argv[] )
{
	GtkWidget *window;
	GtkWidget *label1;
	GtkWidget *label2;
	GtkWidget *label3;
	GtkWidget *button1;
	GtkWidget *button2;
	GtkWidget *button3;
	GtkWidget *hbox;

	gtk_init( &argc, &argv );

	window = gtk_window_new(GTK_WINDOW_TOPLEVEL);
	label1 = gtk_label_new("Label1");
	label2 = gtk_label_new("Label2");
	label3 = gtk_label_new("Label3");

	button1 = gtk_button_new_with_label("Button 1");
	button2 = gtk_button_new_with_label("Button 2");
	button3 = gtk_button_new_with_label("Button 3");

	hbox = gtk_hbox_new(FALSE, 0);
	gtk_signal_connect( GTK_OBJECT(window), "delete_event", GTK_SIGNAL_FUNC(destroyapp), NULL);
	gtk_signal_connect( GTK_OBJECT(button1), "clicked", GTK_SIGNAL_FUNC(button_clicked), NULL);
	gtk_signal_connect( GTK_OBJECT(button2), "clicked", GTK_SIGNAL_FUNC(button_clicked), NULL);
	gtk_signal_connect( GTK_OBJECT(button3), "clicked", GTK_SIGNAL_FUNC(button_clicked), NULL);

	gtk_box_pack_start(GTK_BOX(hbox), label1, FALSE, FALSE, 2);
	gtk_box_pack_start(GTK_BOX(hbox), button1, FALSE, FALSE, 2);
	gtk_box_pack_start(GTK_BOX(hbox), label2, FALSE, FALSE, 2);
	gtk_box_pack_start(GTK_BOX(hbox), button2, FALSE, FALSE, 2);
	gtk_box_pack_start(GTK_BOX(hbox), label3, FALSE, FALSE, 2);
	gtk_box_pack_start(GTK_BOX(hbox), button3, FALSE, FALSE, 2);

	gtk_container_add(GTK_CONTAINER(window), hbox);

	gtk_container_border_width(GTK_CONTAINER(window), 15);

	gtk_widget_show(hbox);
	gtk_widget_show(label1);
	gtk_widget_show(label2);
	gtk_widget_show(label3);
	gtk_widget_show(button1);
	gtk_widget_show(button2);
	gtk_widget_show(button3);
	gtk_widget_show(window);

	gtk_main();

	return 0;
}


```

This is the error that it spat out.

```

me@me:~$ gcc hbox.c -o hbox
hbox.c:1:21: error: gtk/gtk.h: No such file or directory
hbox.c:2:18: error: glib.h: No such file or directory
hbox.c:4: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘destroyapp’
hbox.c:11: error: expected ‘)’ before ‘*’ token
hbox.c: In function ‘main’:
hbox.c:18: error: ‘GtkWidget’ undeclared (first use in this function)
hbox.c:18: error: (Each undeclared identifier is reported only once
hbox.c:18: error: for each function it appears in.)
hbox.c:18: error: ‘window’ undeclared (first use in this function)
hbox.c:19: error: ‘label1’ undeclared (first use in this function)
hbox.c:20: error: ‘label2’ undeclared (first use in this function)
hbox.c:21: error: ‘label3’ undeclared (first use in this function)
hbox.c:22: error: ‘button1’ undeclared (first use in this function)
hbox.c:23: error: ‘button2’ undeclared (first use in this function)
hbox.c:24: error: ‘button3’ undeclared (first use in this function)
hbox.c:25: error: ‘hbox’ undeclared (first use in this function)
hbox.c:29: error: ‘GTK_WINDOW_TOPLEVEL’ undeclared (first use in this function)
hbox.c:38: error: ‘FALSE’ undeclared (first use in this function)
hbox.c:39: error: ‘destroyapp’ undeclared (first use in this function)
hbox.c:39: error: ‘NULL’ undeclared (first use in this function)
hbox.c:40: error: ‘button_clicked’ undeclared (first use in this function)

```

So, looks like gtk/gtk.h and glib.h are just not present. However, /usr/include/glib-2.0 and /usr/include/gtk-2.0/gtk exist. I tried making a symlink to the gtk directory, but that didn't seem to work. Can you help me? Thanks!

---

### Post by rodo-&gt;dave on 2008-01-06
to compile:

$ gcc `pkg-config --cflags --libs gtk+-2.0` hbox.c -o hbox

---

### Post by Vox754 on 2008-01-06
> **rocketman768 said:**
> I read a thread that said the packages to install were: libgtk2.0-dev, libglade2-dev.

This is the error that it spat out.

```

me@me:~$ **gcc hbox.c -o hbox**
hbox.c:1:21: error: gtk/gtk.h: No such file or directory
hbox.c:2:18: error: glib.h: No such file or directory
...

```

So, looks like gtk/gtk.h and glib.h are just not present. However, /usr/include/glib-2.0 and /usr/include/gtk-2.0/gtk exist. I tried making a symlink to the gtk directory, but that didn't seem to work. Can you help me? Thanks!

New users to the GNU Compiler Collection often don't know that you have to use flags to specify the location of headers and libraries.

[See this thread.](http://ubuntuforums.org/showthread.php?t=567049)

---

### Post by MicahCarrick on 2008-01-06
If you need some help using glade, check out: [GTK+ and Glade3 GUI Programming Tutorial]("http://www.micahcarrick.com/12-24-2007/gtk-glade-tutorial-part-1.html")

Part 3 is coming out in a day or two which includes some description on why you use that pkg-config command withing the gcc command when compiling GTK apps... here's the snippet that will help you:

> In order for gcc to know where the GTK+ libraries are that it needs to link to and what compiler flags to use, we use a program called pkg-config. When we installed the GTK+ development package, a package-config file named 'gtk+-2.0.pc' was installed on our system. This file tells the pkg-config program which version of the GTK+ libraries are installed and where the include files live on our system. To illustrate this, type the following command in your terminal:

pkg-config --modversion gtk+-2.0

The output should show the version of GTK+ you have installed. On my system it shows '2.12.0'. Now let's look at what compiler flags are needed to build a GTK+ application on my system:

pkg-config --cflags gtk+-2.0

The output of that command shows a bunch of -I switches which are specifying include paths for the compiler to use. This will tell gcc where to look for include files when we use '#include' in our application. The very first one on my system is '-I/usr/include/gtk-2.0'. That means that when I use '#include ' in my code, gcc will be able to find '/usr/include/gtk-2.0/gtk/gtk.h'.

Anytime you use a '#include <library/header.h>' style include that is not part of the standard C library in your code, there should be a '-I/path/to/library' style switch passed to gcc.

You should also install devhelp (sudo aptitude install devhelp libgtk2.0-doc) which will allow you to browse and search the API documentation. That can help a lot.

---

### Post by matjaz on 2008-01-07
Thanks, it helped me a lot.

Just a hint for people like me that wonder why it still doesn't work?:confused:
The string `pkg-config --cflags --libs gtk+-2.0` in 
> $ gcc `pkg-config --cflags --libs gtk+-2.0` hbox.c -o hbox
is in backticks ( ` `) , not in " " or ' '.
( And then it works:) )

And a question:
How can i make gcc search that paths in `pkg-config --cflags --libs gtk+-2.0` without having to specify that every time, and if i do it by setting some sort of an environment variable, what kind of effects can that have when i am compiling a program that doesn't need gtk?

And will that make gcc compile my programs when i invoke gcc from eclipse or KDevelop? 

Thanks in advance.

---

### Post by rodo-&gt;dave on 2008-01-07
If I run 
$> pkg-config --cflags --libs gtk+-2.0
I get:
-I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12  -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lgdk_pixbuf-2.0 -lm -lpangocairo-1.0 -lfontconfig -lXext -lXrender -lXinerama -lXi -lXrandr -lXcursor -lXfixes -lpango-1.0 -lcairo -lX11 -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0

now, its a lot easier to use the `pkg-config --cflags --libs gtk+-2.0`

Here is a simple makefile called "makefile"

```
CC = gcc

CFLAGS = -g -Wall `pkg-config --cflags --libs gtk+-2.0`

PROG = hbox

SRCS = 	hbox.c 

all:	$(PROG)

$(PROG):     $(SRCS)
	$(CC) -o $(PROG) $(SRCS) $(CFLAGS)

clean:
	rm -f *.o *~

```

so you could just type 
$> make 
at the command prompt (after creating the makefile file in the same dir as your hbox.c)
and it *should* build the example program you listed (note: the should :)

if you type:
$> make clean
it would run the rm command

I don't know anything about eclipse :(

Also, check out what Micah Carrick wrote, he has helped me many times over the last few weeks at [www.gtkforums.com](www.gtkforums.com)

---

### Post by Vox754 on 2008-01-07
> **matjaz said:**
> 
Just a hint for people like me that wonder why it still doesn't work?:confused:
The string `pkg-config --cflags --libs gtk+-2.0` in 

is in backticks ( ` `) , not in " " or ' '.
( And then it works:) )


For a discussion on backticks [read this thread.](http://ubuntuforums.org/showthread.php?t=643901)

> **matjaz said:**
> 
And a question:
How can i make gcc search that paths in `pkg-config --cflags --libs gtk+-2.0` without having to specify that every time, and if i do it by setting some sort of an environment variable, what kind of effects can that have when i am compiling a program that doesn't need gtk?

As rodo->dave points out, this is exactly the job which "make" was created for.
This program searches a file, usually named "Makefile" or "makefile", which contains the needed commands to properly build all object files and executables.
In your case you would use a bunch of "gcc" commands to build all your sources. However, "make" is a general utility which works for other programming languages as well and works this way: it updates a "target" if its "prerequisites" have changed.

In rodo->dave's example the target "hbox" (the executable) is updated (recompiled) if its dependency "hbox.c" (the source) is modified. All those $(VARIABLES) are expanded to generate the full "gcc" command.

As with everything, you can create huge complicated makefiles, but for small projects one makefile with just one target is all you need to produce one single executable.

The GCC manual and the Make manual are in the repositories, search them through Synaptic. They are big and have lots of information. There's no need to read them all, but may be useful as references.
```

sudo aptitude install gcc-doc make-doc

```
They live in
```

/usr/share/doc

```
as html documents.

> **matjaz said:**
> 
And will that make gcc compile my programs when i invoke gcc from eclipse or KDevelop? 

IDEs just add flags to the basic "gcc" command through pretty graphical interfaces of some sort.
So if you don't specify anything it's just
```

gcc file_name.c

```
But when you add library paths and other options, the command might change as
```

gcc file_name.c -o file_name -g -Wall -O2 -I/my/path/include -L/my/path/lib -L/my/other/path/lib -lmylib -lmylib2

```

Learn to use the command line, then you'll understand what IDEs do in the background for you.

---

