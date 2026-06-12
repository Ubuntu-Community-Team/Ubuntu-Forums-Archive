---
title: "How do I &quot;launch&quot; my &quot;Hello World&quot; script written in C?"
date: 2009-11-11
forum: Programming Talk
---

### Post by asuastrophysics on 2009-11-11
Hey everyone,

I'm a complete noob to programming, know nothing about it other than a wiki article [_here_]("http://en.wikipedia.org/wiki/C_%28programming_language%29") and a few articles the admin staff posted about making effective threads in this section.

(I'm going to sound like an idiot) Just out of curiosity, how do I launch this "Hello World" script written in C for GTK+ ?  
[PHP] #include <gtk/gtk.h>
 
 int main (int argc, char *argv[])
 {
    GtkWidget *window;
    GtkWidget *label;
 
    gtk_init (&argc, &argv);
 
    /* create the main, top level, window */
    window = gtk_window_new (GTK_WINDOW_TOPLEVEL);
 
    /* give it the title */
    gtk_window_set_title (GTK_WINDOW (window), "Hello World");
 
    /* Connect the destroy signal of the window to gtk_main_quit
     * When the window is about to be destroyed we get a notification and
     * stop the main GTK+ loop
     */
    g_signal_connect (window, "destroy",
                      G_CALLBACK (gtk_main_quit), NULL);
 
    /* Create the "Hello, World" label  */
    label = gtk_label_new ("Hello, World");
 
    /* and insert it into the main window  */
    gtk_container_add (GTK_CONTAINER (window), label);
 
    /* make sure that everything, window and label, are visible */
    gtk_widget_show_all (window);
 
    /* start the main loop, and let it rest there until the application is closed */
    gtk_main ();
 
    return 0;
 }
[/PHP]

I tried launching it as:
```
sh <filename of hello world>
```

But that didn't seem to work. Can someone help me through my stupidity? 

Thanks for any help in advance!!! :D

---

### Post by jediborger on 2009-11-11
Well C is a compiled language so it must first be compiled using some like 
```
gcc myprogram.c -o myprogram
```
The first arg is the "script" as you referred to it and then a name for the output program then you can execute the program on the command line. Note for GTK and most gui stuff you will need to include some headers which I don't remember what you need off the top of my head. But you should do a bit more reading. If you are looking for an interpreted language check out Python, Perl or Ruby, all of which have GTK bindings.

---

### Post by asuastrophysics on 2009-11-11
Thanks! :popcorn:
 I'll try to research which headers I need to compile this.

---

### Post by jediborger on 2009-11-11
Ok so after a little refresher I can help you out with this particular program. Here's the commands:
```
gcc myprogram.c -o myprogram `pkg-config --cflags --libs gtk+-x11-2.0`
./myprogram
```
In a nutshell C must be compiled, typically using gcc then you can run it. As I said before the gtk gui kit requires some header files, think of the include line at the top of the c program. So the pkg-config program fetches those for you. You can see all your configured libraries by running:
```
pkg-config --list-all
```
But as you said you are new at this. Definitely read more. I have found [http://cprogramming.com]("http://cprogramming.com") a good resource with nice tutorials. Also check out the programming section of the Ubuntu Forums, there is a ton of stuff there designed to help out new programmers.

---

### Post by asuastrophysics on 2009-11-11
thanks for your help!

---

