---
title: "Looking to get GTK Hello World working ..."
date: 2009-01-10
forum: Programming Talk
---

### Post by dbee on 2009-01-10
I'm just messing about with linux application programming. I'm trying to get GTK hello world to work ...

I've installed libgtk1.2-dev and saved this code as hello.c ...

```

#include <config.h>
#include </usr/include/gtk-1.2/gtk/gtk.h>

/*
 * Terminate the main loop.
 */
static void
on_destroy (GtkWidget * widget, gpointer data)
{
    gtk_main_quit ();
}

int
main (int argc, char *argv[])
{
   GtkWidget *window;
   GtkWidget *label;

   gtk_init (&argc, &argv);

   /* create the main, top level, window */
   window = gtk_window_new (GTK_WINDOW_TOPLEVEL);

   /* give the window a 20px wide border */
   gtk_container_set_border_width (GTK_CONTAINER (window), 20);

   /* give it the title */
   gtk_window_set_title (GTK_WINDOW (window), PACKAGE " " VERSION);

   /* open it a bit wider so that both the label and title show up */
   gtk_window_set_default_size (GTK_WINDOW (window), 200, 50);

   /* load the icon for the window; here we just load one, default icon */
   gtk_window_set_default_icon_from_file (PIXMAPS_DIR "/hello-icon.gif",
                                           NULL);

   /* Connect the destroy event of the window with our on_destroy function
    * When the window is about to be destroyed we get a notificaiton and
    * stop the main GTK loop
    */
   g_signal_connect (G_OBJECT (window), "destroy",
                     G_CALLBACK (on_destroy), NULL);

   /* Create the "Hello, World" label  */
   label = gtk_label_new ("Hello, World");

   /* and insert it into the main window  */
   gtk_container_add (GTK_CONTAINER (window), label);

   /* make sure that everything, window and label, are visible */
   gtk_widget_show_all (window);

   /* start the main loop */
   gtk_main ();

   return 0;
}


```

Now i've simply done a 

```

babo@eire:~$ gcc hello.c -o hello
hello.c:1:20: error: config.h: No such file or directory
In file included from hello.c:2:
/usr/include/gtk-1.2/gtk/gtk.h:31:21: error: gdk/gdk.h: No such file or directory
/usr/include/gtk-1.2/gtk/gtk.h:32:31: error: gtk/gtkaccelgroup.h: No such file or directory
/usr/include/gtk-1.2/gtk/gtk.h:33:31: error: gtk/gtkaccellabel.h: No such file or directory
/usr/include/gtk-1.2/gtk/gtk.h:34:31: error: gtk/gtkadjustment.h: No such file or directory
/usr/include/gtk-1.2/gtk/gtk.h:35:30: error: gtk/gtkalignment.h: No such file or directory
/usr/include/gtk-1.2/gtk/gtk.h:36:24: error: gtk/gtkarg.h: No such file or directory
/usr/include/gtk-1.2/gtk/gtk.h:37:32: error: gtk/gtkaspectframe.h: No such file or directory
/usr/include/gtk-1.2/gtk/gtk.h:38:26: error: gtk/gtkarrow.h: No such file or directory
....................
/usr/include/gtk-1.2/gtk/gtk.h:137:27: error: gtk/gtkwindow.h: No such file or directory
hello.c:8: error: expected ‘)’ before ‘*’ token
hello.c: In function ‘main’:
hello.c:16: error: ‘GtkWidget’ undeclared (first use in this function)
hello.c:16: error: (Each undeclared identifier is reported only once
hello.c:16: error: for each function it appears in.)
hello.c:16: error: ‘window’ undeclared (first use in this function)
hello.c:17: error: ‘label’ undeclared (first use in this function)
hello.c:22: error: ‘GTK_WINDOW_TOPLEVEL’ undeclared (first use in this function)
hello.c:28: error: ‘PACKAGE’ undeclared (first use in this function)
hello.c:28: error: expected ‘)’ before string constant
hello.c:34: error: ‘PIXMAPS_DIR’ undeclared (first use in this function)
hello.c:34: error: expected ‘)’ before string constant
hello.c:42: error: ‘on_destroy’ undeclared (first use in this function)
hello.c:42: error: ‘NULL’ undeclared (first use in this function)

```

I've confirmed gtk.h exists. I'm also clueless about config.h. Which config.h are we talking about here ? Do i need to write it ?

Sorry for being clueless, but i'd love to get a demo of this working ...

---

### Post by MadMan2k on 2009-01-10
it seems like you are trying to use C for GUI programming. This is a big mistake - you should use some programming language instead.

Here is the hello world in python:

```
#!/usr/bin/env python
import gtk

def main():
    win = gtk.Window()
    win.set_title("Hello World Program")
    win.add(gtk.Label("Hello World!"))
    win.show_all()
    gtk.main()

main()
```

---

### Post by SledgeHammer_999 on 2009-01-10
> **dbee said:**
> I'm just messing about with linux application programming. I'm trying to get GTK hello world to work ...

I've installed libgtk1.2-dev and saved this code as hello.c ...

```

#include <config.h>
#include </usr/include/gtk-1.2/gtk/gtk.h>

/*
 * Terminate the main loop.
 */
static void
on_destroy (GtkWidget * widget, gpointer data)
{
    gtk_main_quit ();
}

int
main (int argc, char *argv[])
{
   GtkWidget *window;
   GtkWidget *label;

   gtk_init (&argc, &argv);

   /* create the main, top level, window */
   window = gtk_window_new (GTK_WINDOW_TOPLEVEL);

   /* give the window a 20px wide border */
   gtk_container_set_border_width (GTK_CONTAINER (window), 20);

   /* give it the title */
   gtk_window_set_title (GTK_WINDOW (window), PACKAGE " " VERSION);

   /* open it a bit wider so that both the label and title show up */
   gtk_window_set_default_size (GTK_WINDOW (window), 200, 50);

   /* load the icon for the window; here we just load one, default icon */
   gtk_window_set_default_icon_from_file (PIXMAPS_DIR "/hello-icon.gif",
                                           NULL);

   /* Connect the destroy event of the window with our on_destroy function
    * When the window is about to be destroyed we get a notificaiton and
    * stop the main GTK loop
    */
   g_signal_connect (G_OBJECT (window), "destroy",
                     G_CALLBACK (on_destroy), NULL);

   /* Create the "Hello, World" label  */
   label = gtk_label_new ("Hello, World");

   /* and insert it into the main window  */
   gtk_container_add (GTK_CONTAINER (window), label);

   /* make sure that everything, window and label, are visible */
   gtk_widget_show_all (window);

   /* start the main loop */
   gtk_main ();

   return 0;
}


```

Now i've simply done a 

```

babo@eire:~$ gcc hello.c -o hello
hello.c:1:20: error: config.h: No such file or directory
In file included from hello.c:2:
/usr/include/gtk-1.2/gtk/gtk.h:31:21: error: gdk/gdk.h: No such file or directory
/usr/include/gtk-1.2/gtk/gtk.h:32:31: error: gtk/gtkaccelgroup.h: No such file or directory
/usr/include/gtk-1.2/gtk/gtk.h:33:31: error: gtk/gtkaccellabel.h: No such file or directory
/usr/include/gtk-1.2/gtk/gtk.h:34:31: error: gtk/gtkadjustment.h: No such file or directory
/usr/include/gtk-1.2/gtk/gtk.h:35:30: error: gtk/gtkalignment.h: No such file or directory
/usr/include/gtk-1.2/gtk/gtk.h:36:24: error: gtk/gtkarg.h: No such file or directory
/usr/include/gtk-1.2/gtk/gtk.h:37:32: error: gtk/gtkaspectframe.h: No such file or directory
/usr/include/gtk-1.2/gtk/gtk.h:38:26: error: gtk/gtkarrow.h: No such file or directory
....................
/usr/include/gtk-1.2/gtk/gtk.h:137:27: error: gtk/gtkwindow.h: No such file or directory
hello.c:8: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
hello.c: In function &#8216;main&#8217;:
hello.c:16: error: &#8216;GtkWidget&#8217; undeclared (first use in this function)
hello.c:16: error: (Each undeclared identifier is reported only once
hello.c:16: error: for each function it appears in.)
hello.c:16: error: &#8216;window&#8217; undeclared (first use in this function)
hello.c:17: error: &#8216;label&#8217; undeclared (first use in this function)
hello.c:22: error: &#8216;GTK_WINDOW_TOPLEVEL&#8217; undeclared (first use in this function)
hello.c:28: error: &#8216;PACKAGE&#8217; undeclared (first use in this function)
hello.c:28: error: expected &#8216;)&#8217; before string constant
hello.c:34: error: &#8216;PIXMAPS_DIR&#8217; undeclared (first use in this function)
hello.c:34: error: expected &#8216;)&#8217; before string constant
hello.c:42: error: &#8216;on_destroy&#8217; undeclared (first use in this function)
hello.c:42: error: &#8216;NULL&#8217; undeclared (first use in this function)

```

I've confirmed gtk.h exists. I'm also clueless about config.h. Which config.h are we talking about here ? Do i need to write it ?

Sorry for being clueless, but i'd love to get a demo of this working ...

First of all install "libgtk2.0-dev"
Then change "#include </usr/include/gtk-1.2/gtk/gtk.h>" to "#include <gtk/gtk.h>"
And then compile using:
```
gcc -Wall -g hello.c -o helloworld `pkg-config --cflags gtk+-2.0` `pkg-config --libs gtk+-2.0`
```
or
```

gcc -Wall -g hello.c -o helloworld `pkg-config --cflags --libs gtk+-2.0`
```
Take a look at this guide: [http://library.gnome.org/devel/gtk-tutorial/stable/](http://library.gnome.org/devel/gtk-tutorial/stable/)

EDIT: Just tested your code and it can't compile... Maybe it needs the gtk-1 instead of gtk-2. Can't test it though right now

---

### Post by Zugzwang on 2009-01-10
> **MadMan2k said:**
> it seems like you are trying to use C for GUI programming. This is a big mistake - you should use some programming language instead.


Interesting. I always thought that C *is* a programming language. :-\"

---

### Post by Nher on 2009-01-10
Google for autotools if you want to know about config.h. You can find a gtk tutorial and hello world at [http://library.gnome.org/devel/gtk-tutorial/stable/](http://library.gnome.org/devel/gtk-tutorial/stable/).

---

### Post by mali2297 on 2009-01-10
> **dbee said:**
> I'm just messing about with linux application programming. I'm trying to get GTK hello world to work ...

I've installed libgtk1.2-dev and saved this code as hello.c ...


You have installed an older version of GTK+. Most applications use GTK+ 2.0 these days. You probably want the package **libgtk2.0-dev** instead.

There are some useful links to tutorials and other resources at [http://www.gtk.org/documentation.html](http://www.gtk.org/documentation.html).

---

### Post by eye208 on 2009-01-10
> **MadMan2k said:**
> it seems like you are trying to use C for GUI programming. This is a big mistake - you should use some programming language instead.

Here is the hello world in python:

```
#!/usr/bin/env python
import gtk

def main():
    win = gtk.Window()
    win.set_title("Hello World Program")
    win.add(gtk.Label("Hello World!"))
    win.show_all()
    gtk.main()

main()
```
Typical Python fanboy comment.

The funny thing about Python fanboys is that they can't even get Hello World right. The program above doesn't perform any event handling. After closing its window, the process will remain in memory indefinitely.

Even more funny: Once the event handling is added, the Python version will be no shorter than the C version:
```
#include <gtk/gtk.h>

int main(int argc, char **argv) {
	gtk_init(&argc, &argv);
	GtkWindow* win = gtk_window_new(GTK_WINDOW_TOPLEVEL);
	gtk_window_set_title(win, "Hello World Program");
	gtk_container_add(win, gtk_label_new("Hello World!"));
	gtk_widget_show_all(win);
	g_signal_connect(win, "delete_event", gtk_main_quit, NULL);
	gtk_main();
	return 0;
}
```

---

### Post by MadMan2k on 2009-01-10
yeah, right I forgot the delete-event... :(

but lets do some real python fanboyism: lets suppose we want to write a maintanable programm and use some Software Engineering

```
#!/usr/bin/env python
import gtk

class HelloWindow(gtk.Window):
    def __init__(self, widget):
         gtk.Window.__init__(self)
         self.set_title("Hello World Program")
         self.connect("delete-event", self.quit)
         self.add(widget)
         self.show_all()    

    def quit(self):
         gtk.main_quit()

def main():
    w = HelloWindow(gtk.Label("Hello World!"))
    gtk.main()

main()
```
now do that in C... ;)

---

### Post by mike_g on 2009-01-10
So by adding a class you have suddenly made your program maintainable? Gtk in itself implements many of the more useful OOP feature.

I prefer using PyGtk to Gtk as it is because I find it more productive, but you really arent providing a good argument for python here.

I find the most verbose thing with Gtk is passing data to callbacks. In C this means you have to predefine a new struct for (nearly) each callback you want to pass multiple parameters to.

---

### Post by eye208 on 2009-01-11
> **MadMan2k said:**
> but lets do some real python fanboyism: lets suppose we want to write a maintanable programm and use some Software Engineering

```
#!/usr/bin/env python
import gtk

class HelloWindow(gtk.Window):
    def __init__(self, widget):
         gtk.Window.__init__(self)
         self.set_title("Hello World Program")
         self.connect("delete-event", self.quit)
         self.add(widget)
         self.show_all()    

    def quit(self):
         gtk.main_quit()

def main():
    w = HelloWindow(gtk.Label("Hello World!"))
    gtk.main()

main()
```
now do that in C... ;)
Here we go.
```
#include <gtkmm.h>
using namespace Gtk;

struct HelloWindow : public Window {
    HelloWindow(Widget& widget) {
        set_title("Hello World Program");
        signal_delete_event().connect(sigc::mem_fun(this, &HelloWindow::quit));
        add(widget);
        show_all();
    }
    bool quit(GdkEventAny* event) { Main::quit(); }
};

int main(int argc, char **argv) {
    Main kit(argc, argv);
    Label label("Hello World!");
    HelloWindow w(label);
    kit.run();
}
```
You know, just recently another Python fanboy on this forum [tried to convince me](http://ubuntuforums.org/showthread.php?p=6523077#post6523077) that C/C++ requires 5 lines of code to do what Python does in just 1 line. I'm still waiting for evidence to back up this claim. Looking at these examples, I must admit that Python leaves me unimpressed.

---

### Post by PmDematagoda on 2009-01-11
> **mali2297 said:**
> You have installed an older version of GTK+. Most applications use GTK+ 2.0 these days. You probably want the package **libgtk2.0-dev** instead.

There are some useful links to tutorials and other resources at [http://www.gtk.org/documentation.html](http://www.gtk.org/documentation.html).

If the program is simple enough, then there is a good chance that you can compile the program with both GTK+-1.2 and 2.0(I did that :)). The reason why those errors showed up was probably because the header was invalid and the OP did not use the correct arguments to GCC.

And let's please not discuss how Python is greater than C or the other way around, fact is that both programming languages have their uses and advantages and keep it at that.

---

### Post by MadMan2k on 2009-01-11
> **eye208 said:**
> Here we go.
```
#include <gtkmm.h>
using namespace Gtk;

struct HelloWindow : public Window {
    HelloWindow(Widget& widget) {
        set_title("Hello World Program");
        signal_delete_event().connect(sigc::mem_fun(this, &HelloWindow::quit));
        add(widget);
        show_all();
    }
    bool quit(GdkEventAny* event) { Main::quit(); }
};

int main(int argc, char **argv) {
    Main kit(argc, argv);
    Label label("Hello World!");
    HelloWindow w(label);
    kit.run();
}
```
You know, just recently another Python fanboy on this forum [tried to convince me](http://ubuntuforums.org/showthread.php?p=6523077#post6523077) that C/C++ requires 5 lines of code to do what Python does in just 1 line. I'm still waiting for evidence to back up this claim. Looking at these examples, I must admit that Python leaves me unimpressed.
I know that C++ is quite expressive - especially if you add boost to it. But I was asking for C code, since thats the evil ;)

I could also provide some examples where Python is much more expressive than C++, but that would come down to some corner cases using array slicing and numpy.

---

### Post by eye208 on 2009-01-11
> **MadMan2k said:**
> I know that C++ is quite expressive - especially if you add boost to it. But I was asking for C code, since thats the evil ;)
Given the fact that C++ existed 8 years earlier than Python, I think it's only fair to use that for comparison. Besides, I already proved that even the C version is shorter than the Python version. What's next? Will you ask me to use COBOL on punch cards to make Python look less pathetic? ;)

---

### Post by MadMan2k on 2009-01-11
> **eye208 said:**
> Given the fact that C++ existed 8 years earlier than Python, I think it's only fair to use that for comparison. Besides, I already proved that even the C version is shorter than the Python version. What's next? Will you ask me to use COBOL on punch cards to make Python look less pathetic? ;)
basically my point is that C programms are hard to maintain and therefore you should not write new programs in it. I once tried to update some OSS project written in C and finally gave up because it was to tiresome to look up the method names, because there was no inheritance.

Out of C++ and Python, Python is without a doubt the more advanced language and therefore one should use it **unless** you really need the speed advantage of C++, but you dont need it for GUI applications.

I will likely write some more sophisticated article on this topic..

---

### Post by eye208 on 2009-01-12
> **MadMan2k said:**
> basically my point is that C programms are hard to maintain and therefore you should not write new programs in it. I once tried to update some OSS project written in C and finally gave up because it was to tiresome to look up the method names, because there was no inheritance.
You may be surprised to hear this, but one reason why people like to use C is because it keeps people like you from messing with their code. Here's a famous quote from a guy whose name may sound familiar to you:

> **Linus Torvalds]C++ is a horrible language. It's made more horrible by the fact that a lot of substandard programmers use it, to the point where it's much much easier to generate total and utter crap with it. Quite frankly, even if the choice of C were to do *nothing* but keep the C++ programmers out, that in itself would be a huge reason to use C.

In other words: the choice of C is the only sane choice. I know Miles Bader jokingly said "to piss you off", but it's actually true. I've come to the conclusion that any programmer that would prefer the project to be in C++ over C is likely a programmer that I really *would* prefer to piss off, so that he doesn't come and screw up any project I'm involved with.[/quote]
There's another reason why many people still prefer C over high-level languages: C won't do anything behind your back. If you look at a piece of C code, you immediately see what it does. No hidden constructor/destructor calls. No function calls hidden behind overloaded operators. Every function call is visible, and every function name is unique and independent from context. You can see what's going on, at all times. This, by the way, makes it an ideal language for beginners.

That doesn't mean that OOP is bad. It's perfectly possible to apply OOP principles in C. GTK works like that. PyGtk and gtkmm are just wrappers. GTK itself is implemented in C.

> Out of C++ and Python, Python is without a doubt the more advanced language and therefore one should use it **unless** you really need the speed advantage of C++, but you dont need it for GUI applications.
You wouldn't want to use a word processor or web browser written in Python. Trust me on this.  said:**
> I will likely write some more sophisticated article on this topic..
I'm looking forward to it, but please, do it in your own thread. Your comments here have been way off topic from the very beginning.

---

### Post by module0000 on 2009-01-18
I code in Python, C, and C++.

Python is a great hobby language, but it's just that, a *hobby language*.  It's nice for proof-of-concept tools you whip up in a day, but noone publishes enterprise and commercial software written in an *interpreted* language.  That's like me trying to put my latest and greatest BASH scripts on the shelf at Best Buy.

On the other hand, your operating system is written in C.  Game over.

---

### Post by ridgeland on 2009-02-20
Thanks dbee for starting this thread. I had the same issue.  With the latest libgtk2.0-dev (2.14.4) from synaptic I still could not get gtk examples to compile. I got 
gtk/gtk.h: no such file
no matter what I tried with #include.
Thanks SledgeHammer_999.  With the gcc command line my programs complied without error and ran fine.
My next challenge is to learn to do this with anjuta or geany.

---

### Post by Gordon Bennett on 2009-02-21
> **ridgeland said:**
> Thanks dbee for starting this thread. I had the same issue.  With the latest libgtk2.0-dev (2.14.4) from synaptic I still could not get gtk examples to compile. I got 
gtk/gtk.h: no such file
no matter what I tried with #include.
Thanks SledgeHammer_999.  With the gcc command line my programs complied without error and ran fine.
My next challenge is to learn to do this with anjuta or geany.

Anjuta is great for GTK programming - it can create a GTK/Gnome project for you and sort out all the libraries too.  It even has a built-in GUI editor.

I suggest you use '.glade' files for your project (Anjuta will do this for you when creating a project), as one of the many great things about GTK is that it is very easy to add components to the glade file and tie them to your code.

There's also a fantastic GTK programming tutorial by Micah Carrick: [Micah Carrick's GTK tutorial]("http://www.micahcarrick.com/12-24-2007/gtk-glade-tutorial-part-1.html")

---

### Post by ajackson on 2009-02-21
> **Gordon Bennett said:**
> I suggest you use '.glade' files for your project
I'd go along with this advice, get the GUI leg work done in Glade and worry about the finer points in your program. As for the earlier comments in this thread all I'll say is wow.

---

