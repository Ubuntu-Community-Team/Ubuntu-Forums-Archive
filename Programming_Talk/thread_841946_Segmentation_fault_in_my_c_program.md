---
title: "Segmentation fault in my c program"
date: 2008-06-26
forum: Programming Talk
---

### Post by lorderico on 2008-06-26
This is my code:

#include <stdio.h>
#include <gtk/gtk.h>
	GtkWidget		*open;
	GtkWidget		*save;
	GtkWidget		*new;
	int			saved=0;
void 
on_window_destroy (GtkObject *object, gpointer user_data)
{
	printf("Here\n");
        gtk_main_quit();
}
void 
on_new_menu_item_activate (GtkObject *object, gpointer user_data)
{
	printf("Here2\n");
	gtk_widget_show (new);
}
void 
on_open_menu_item_activate (GtkObject *object, gpointer user_data)
{
	printf("Here3\n");
	gtk_widget_show (open);
}
void 
on_save_menu_item_activate (GtkObject *object, gpointer user_data)
{
	printf("Here4\n");
	if (!saved){
		gtk_widget_show (save);
		saved=TRUE;
	}
	else{}
}
void 
on_save_as_menu_item_activate (GtkObject *object, gpointer user_data)
{
	printf("Here4\n");
        gtk_widget_show (save);
} 
int
main (int argc, char *argv[])
{
        GtkBuilder              *builder;
        GtkWidget               *window;
	
	saved=0;
        //printf("here\n");
	//return 0;
 
        gtk_init (&argc, &argv);

        builder = gtk_builder_new ();
        gtk_builder_add_from_file (builder, "tutorial.xml", NULL);

        window = GTK_WIDGET (gtk_builder_get_object (builder, "window"));
        
	open = GTK_WIDGET (gtk_builder_get_object (builder, "openchooserdialog"));
	save = GTK_WIDGET (gtk_builder_get_object (builder, "savechooserdialog"));
	new = GTK_WIDGET (gtk_builder_get_object (builder, "newchooserdialog"));

	gtk_builder_connect_signals (builder, NULL); 
        g_object_unref (G_OBJECT (builder));
        gtk_widget_show (window);
	//printf("here2\n");      
        gtk_main ();
        return 0;
}

It compiles fine, but when I run it I get a segmantation fault.  Any idea why?  I don't really even know what a segmentation fault is or what causes it.  I read wikipedia, but I don't know how to apply it.  If only I got a more specific error....
Thanks,
Eric

---

### Post by Wybiral on 2008-06-26
To preserve spacing/indentation in your post, wrap your code in the "[ code ]" tags so we can easily read it.

---

### Post by Can+~ on 2008-06-26
You don't know what a segmentation fault is, and you're using gtk?

Tip: Learn the language, stick to console applications, and once that is under control, start with GTK... or any other toolkit.

---

### Post by ellingsworthorpleton on 2008-06-26
I'll bet you anything it's your gtk_init(). Check out this post:

[http://mail.gnome.org/archives/gtk-list/2006-April/msg00143.html](http://mail.gnome.org/archives/gtk-list/2006-April/msg00143.html)

---

### Post by JupiterV2 on 2008-06-26
> **ellingsworthorpleton said:**
> I'll bet you anything it's your gtk_init(). Check out this post:

[http://mail.gnome.org/archives/gtk-list/2006-April/msg00143.html](http://mail.gnome.org/archives/gtk-list/2006-April/msg00143.html)

The post you linked to was in regards to linking to the wrong, or outdated, gthread library. Perhaps you linked to the wrong thread?

---

### Post by JupiterV2 on 2008-06-27
> **lorderico said:**
> It compiles fine, but when I run it I get a segmantation fault.  Any idea why?  I don't really even know what a segmentation fault is or what causes it.  I read wikipedia, but I don't know how to apply it.  If only I got a more specific error....
Thanks,
Eric

2 things would really help to assist you in debugging your code:

1. As Wybiral has already requested, please post code with the [CODE] or [PHP] tags to retain formatting.

2. Print some debug code detailing the runtime stages of you code. That way you can narrow down where to error is occurring and, hopefully, what may potential be the guilty party.

---

### Post by dwhitney67 on 2008-06-27
Consider using a debugger to step through the code as it is executed.  My preferred interface for the 'gdb' (GNU debugger) is 'ddd'.  It is useful for debugging C and C++ applications, and perhaps others (??).
```
$ sudo apt-get install ddd
$ gcc -g -Wall -pedantic -std=c99 MyProg.c -o MyProg
$ ddd MyProg &
```
The -g option instructs the gcc compiler to retain (include) the symbolic information of the source code in the final executable application.  This is essential when debugging a piece of code.

---

### Post by nvteighen on 2008-06-27
Excuse me, is this a program of yours or someone else's? Yes, it compiles; I don't get a segfault, but this instead:

```

(a:8980): Gtk-CRITICAL **: gtk_widget_show: assertion `GTK_IS_WIDGET (widget)' failed

```

("a" is the name I gave to the executable)

EDIT: Ah, if your trying to learn GTK+ without having strong C skills, you won't go too far...

---

### Post by sshuber on 2008-06-27
Cleaned this up for you:

```
#include <stdio.h>
#include <gtk/gtk.h>
	GtkWidget		*open;
	GtkWidget		*save;
	GtkWidget		*new;
	int			saved=0;
void 
on_window_destroy (GtkObject *object, gpointer user_data)
{
	printf("Here\n");
        gtk_main_quit();
}
void 
on_new_menu_item_activate (GtkObject *object, gpointer user_data)
{
	printf("Here2\n");
	gtk_widget_show (new);
}
void 
on_open_menu_item_activate (GtkObject *object, gpointer user_data)
{
	printf("Here3\n");
	gtk_widget_show (open);
}
void 
on_save_menu_item_activate (GtkObject *object, gpointer user_data)
{
	printf("Here4\n");
	if (!saved){
		gtk_widget_show (save);
		saved=TRUE;
	}
	else{}
}
void 
on_save_as_menu_item_activate (GtkObject *object, gpointer user_data)
{
	printf("Here4\n");
        gtk_widget_show (save);
} 
int
main (int argc, char *argv[])
{
        GtkBuilder              *builder;
        GtkWidget               *window;
	
	saved=0;
        //printf("here\n");
	//return 0;
 
        gtk_init (&argc, &argv);

        builder = gtk_builder_new ();
        gtk_builder_add_from_file (builder, "tutorial.xml", NULL);

        window = GTK_WIDGET (gtk_builder_get_object (builder, "window"));
        
	open = GTK_WIDGET (gtk_builder_get_object (builder, "openchooserdialog"));
	save = GTK_WIDGET (gtk_builder_get_object (builder, "savechooserdialog"));
	new = GTK_WIDGET (gtk_builder_get_object (builder, "newchooserdialog"));

	gtk_builder_connect_signals (builder, NULL); 
        g_object_unref (G_OBJECT (builder));
        gtk_widget_show (window);
	//printf("here2\n");      
        gtk_main ();
        return 0;
}
```

> 
It compiles fine, but when I run it I get a segmantation fault.  Any idea why?  I don't really even know what a segmentation fault is or what causes it.  I read wikipedia, but I don't know how to apply it.  If only I got a more specific error....
Thanks,
Eric

A segmentation fault, aka a segfault, is what happens when you are trying to work with a memory location that is outside the scope of the variables you're using.

For example:
```

int main()
{
     char hello[3]={'H','I','\0'};
     int *ptr=&hello;
     //right now ptr is pointing to memory address 0 for the hello char array
     ptr=ptr+3;
     printf("Trying to access memory loc 3 of hello. It's value is: %c",*ptr);
     return(0);
}
```

If you try to run this you will get a seg fault since the ptr+3 is setting the location it's trying to access outside of the allocated memory for the hello char array.

I strongly recommend using something like [this guide]("http://www.cs.cf.ac.uk/Dave/C/CE.html").

C is a very powerful language, but the pure ability to try to access any memory location is a double-edged sword. It's great if you know what you're doing, but it can cause major problems if you don't.

Debugging is half the fun of programming though. I'd recommend just screwing around and trying to implement simple sorting algorithms in C using pointers. The way to get better is to really just practice!

Seg faults are no joke! Bask in the glory of [xkcd]("http://xkcd.com/371/").

---

### Post by WW on 2008-06-27
In addition to the above suggestions, you should check the return values of gtk_builder_add_from_file(), gtk_builder_get_object() and any other gtk functions that might return an error condition.  For example, gtk_builder_get_obect() returns NULL if the object can not be found.

---

### Post by lorderico on 2008-06-29
Thanks for pointing out that I am a novice at C and this was my first time posting code here.  I learned to program Java, and I am still transitioning.

Anyway, I tried ddd, but could only figure out from it that I had a segmentation fault somewhere.  I am going to have to learn how to use it better...  Eventually, I commented out lines of code out until the program worked.  What I found out is that the first couple lines of code (the GtkWidget *open etc.) is what causes it.  When those declarations are made inside main, there is no problem, except that they cannot be used by any other functions.  When they are made at the top, it produces a segmentation fault.

I am made this app from this [tutorial]("http://www.micahcarrick.com/01-01-2008/gtk-glade-tutorial-part-3.html") tutorial.  I am going farther then the tutorial.

Thanks,
Eric

---

### Post by dwhitney67 on 2008-06-29
When using using 'ddd', first set a breakpoint near where you think the program is crashing (if you don't know, then the first statement in main() will do).

Then 'run' the program.  The debugger will stop at the breakpoint.

To continue the program, either click on 'Next', or if you want to traverse into a function, 'Step'.

Some third-party libraries (e.g. Gtk+, GNU C library) do not include debugging information, so you will not be able to traverse/examine these.

P.S.  To set a breakpoint, simply double-click on the far-left column of a line of code.

---

