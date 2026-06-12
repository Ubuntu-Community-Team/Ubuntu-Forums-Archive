---
title: "newb on a mission"
date: 2007-09-15
forum: Programming Talk
---

### Post by ant2ne on 2007-09-15
I'm new to programming in gcc & c, but I'm on a mission. 

I got a few questions. Please answer, or linky me to the info. 

how do I change the color of the text displayed on the screen for
```
 printf ("Hello, world!\n");
```How do I make ```
printf ("Hello, world!\n");
```display in its own window, but not another terminal? 

I'm also thining in loops. a main loop, and a second loop that scans the keyboard for input that will interrupt the main loop. How do I do this in C. In Visual Basic I'd just use timers.

---

### Post by j_g on 2007-09-16
> **ant2ne said:**
> how do I change the color of the text displayed on the screen

As I recall, there are some ANSI codes to change console window colors (and some, but not all shells, support them). But honestly, I wouldn't bother. If you're writing a console mode program, then it's not going to be used by an enduser who cares about the "looks" of the program. You'd be better off using a GUI toolkit if you want the output to look nice.

> display in its own window, but not another terminal?

Do you mean something like a message box? In that case, you'll want to use a GUI toolkit such as GTK. You can use the Glade3 program to visually design your user interface, and the libglade library to present it to the user. There are also GTK functions to present a message box. In other words, you won't write a console mode app at all.

> a main loop, and a second loop that scans the keyboard for input that will interrupt the main loop.

Do you mean that you want the "main loop" to be doing something else, while the "second loop" is _simultaneously_ scanning for keys? In that case, you'd start the "second loop" as an additional thread. Check out some articles on pthreads ([http://en.wikipedia.org/wiki/POSIX_Threads]("http://en.wikipedia.org/wiki/POSIX_Threads")). In the second loop, you'd likely inform the main loop (of a keypress_ via a mechanism such as Semaphores.

Or if your main loop is doing some sort of "message loop" with a GUI toolkit such as GTK, the toolkit will have a mechanism for sending an "event/message" to the main loop. But of course, if your main loop is using a GUI toolkit, there would be no reason to have a secondary thread scanning for keypresses. The GUI toolkit will inform you of keypresses. You don't scan for them yourself.

---

### Post by slavik on 2007-09-16
> **j_g said:**
> As I recall, there are some ANSI codes to change console window colors (and some, but not all shells, support them). But honestly, I wouldn't bother. If you're writing a console mode program, then it's not going to be used by an enduser who cares about the "looks" of the program. You'd be better off using a GUI toolkit if you want the output to look nice.



Do you mean something like a message box? In that case, you'll want to use a GUI toolkit such as GTK. You can use the Glade3 program to visually design your user interface, and the libglade library to present it to the user. There are also GTK functions to present a message box. In other words, you won't write a console mode app at all.



Do you mean that you want the "main loop" to be doing something else, while the "second loop" is _simultaneously_ scanning for keys? In that case, you'd start the "second loop" as an additional thread. Check out some articles on pthreads ([http://en.wikipedia.org/wiki/POSIX_Threads]("http://en.wikipedia.org/wiki/POSIX_Threads")). In the second loop, you'd likely inform the main loop (of a keypress_ via a mechanism such as Semaphores.

Or if your main loop is doing some sort of "message loop" with a GUI toolkit such as GTK, the toolkit will have a mechanism for sending an "event/message" to the main loop. But of course, if your main loop is using a GUI toolkit, there would be no reason to have a secondary thread scanning for keypresses. The GUI toolkit will inform you of keypresses. You don't scan for them yourself.
QFT

as for colors on a terminal, curses should be able to do that. as for simple text boxes, I think zenity is for that. :)

---

### Post by gnusci on 2007-09-16
step by step, here something about the colors:

[PHP]
// color.c
// table of colors
/*
\033[22;30m - black
\033[22;31m - red
\033[22;32m - green
\033[22;33m - brown
\033[22;34m - blue
\033[22;35m - magenta
\033[22;36m - cyan
\033[22;37m - gray
\033[01;30m - dark gray
\033[01;31m - light red
\033[01;32m - light green
\033[01;33m - yellow
\033[01;34m - light blue
\033[01;35m - light magenta
\033[01;36m - light cyan
\033[01;37m - white
*/

int main(void){
    printf("Hello, world!\n");
    printf("\033[22;34mHello, world!\n");
    printf("\033[22;31mHello, world!\n");
    printf("\033[22;32mHello, world!\n");
return 0;
}

[/PHP]

But also suggest you to use ncurses, using printing colour escape sequences directly for console rendering can make your code unportable.

[http://www.gnu.org/software/ncurses/](http://www.gnu.org/software/ncurses/)
[http://www.tldp.org/HOWTO/text/NCURSES-Programming-HOWTO](http://www.tldp.org/HOWTO/text/NCURSES-Programming-HOWTO)

Here more information about terminal 

[http://www.bigwebmaster.com/General/Howtos/Bash-Prompt-HOWTO/x329.html](http://www.bigwebmaster.com/General/Howtos/Bash-Prompt-HOWTO/x329.html)
[http://www.gilesorr.com/bashprompt/howto/c327.html](http://www.gilesorr.com/bashprompt/howto/c327.html)
[http://www.linuxhowtos.org/Tips%20and%20Tricks/ansi_escape_sequences.htm](http://www.linuxhowtos.org/Tips%20and%20Tricks/ansi_escape_sequences.htm)

---

### Post by ant2ne on 2007-09-16
Good info thanks!

If I wasn't so hung over today I'm certain that I'd make some good progress on my program.

I've been programming in visual basic for years, and have wanted to take the plunge into C. I learned visual basic by examining code, and cutting and pasting. So the posted and linked code helps a lot!!

```
antsvr@antubuntu:~$ sudo apt-get install GTK
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package GTK
antsvr@antubuntu:~$ 
```Is GTK under a different name?

> But also suggest you to use ncurses, using printing colour escape sequences directly for console rendering can make your code unportable."unportable", what does that mean? Is ncurses a library or add on for gcc? 

Here is line 11
```
char c = 'PS1="\[\033[34m\][\$(date +%H%M)][\u@\h:\w]$ ");'
```
Here is an error message
```
antsvr@antubuntu:~/c$ gcc -Wall scrsvr.c -o scrsvr
scrsvr.c:11:10: warning: unknown escape sequence '\]'
scrsvr.c:11:10: warning: unknown escape sequence '\$'
scrsvr.c:11:10: warning: universal character names are only valid in C++ and C99
scrsvr.c:11:10: error: incomplete universal character name \u
scrsvr.c:11:10: warning: unknown escape sequence '\h'
scrsvr.c:11:10: warning: unknown escape sequence '\w'
scrsvr.c:11:10: warning: character constant too long for its type
scrsvr.c: In function ‘main’:
scrsvr.c:11: warning: overflow in implicit constant conversion
scrsvr.c:11: warning: unused variable ‘c’
antsvr@antubuntu:~/c$ 

```

I would also like to learn how to handle hardware interrupts. For now I would just like to scan keyboard and mouse for an interrupt. But I would like to listen to other hardware in the future. Some good linky or info on that would be great.

---

### Post by Wybiral on 2007-09-16
ncurses is a library.

And for console apps it is practically a must (unless you're just streaming out simple data to the terminal).

It lets you control colors/position/keypresses... etc.

---

### Post by ant2ne on 2007-09-16
> **j_g said:**
> Do you mean something like a message box? In that case, you'll want to use a GUI toolkit such as GTK. You can use the Glade3 program to visually design your user interface, and the libglade library to present it to the user. There are also GTK functions to present a message box. In other words, you won't write a console mode app at all.Would someone PLEASE tell me how to install GTK. The download and manually make make install is a nightmare with all its depends. Is there a simple apt-get? Or an install script or something?

---

### Post by slavik on 2007-09-17
open synaptic and look for libgtk-2.0 :)

---

### Post by ant2ne on 2007-09-22
> **slavik said:**
> open synaptic and look for libgtk-2.0 :)
```

antsvr@antubuntu:~/c$ sudo apt-get install libgtk-2.0
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libgtk-2.0
antsvr@antubuntu:~/c$ 
```

---

### Post by slavik on 2007-09-22
> **ant2ne said:**
> ```

antsvr@antubuntu:~/c$ sudo apt-get install libgtk-2.0
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libgtk-2.0
antsvr@antubuntu:~/c$ 
```
you obviously didn't follow my advice. :)

---

### Post by ant2ne on 2007-09-23
> **slavik said:**
> you obviously didn't follow my advice. :)Actually, A search in Synaptic for libgtk-2.0 didn't show me anything. A search for just libgtk discovered several installed packages including...

libgtk2-perl
libgtkhtml3.14-19
libgtkhtml2-0
libgtk2.0-0
libgtk2.0-0-bin
libgtk2.0-0-common
libgtk2.0-0-dev
libgtk2.0-0-doc
libgtk2.0-0-cil
libgtkspell0
libgtksourceview1.0-0
libgtksourceview-common
libgtk1.2
libgtk1.2common

So I guess I don't know, what it is that I'm missing.

---

### Post by Modred on 2007-09-23
If all of the listed package are installed, then you should be able to write programs using gtk2.

Unless I'm mistaken, libgtk2.0.0-bin and libgtk2.0.0-common are used for running gtk2 based programs, and libgtk2.0.0-dev provides the sources for you to link against when creating programs.

---

### Post by gnusci on 2007-09-23
I see you have all the necessary stuff to compile gtk code...

---

### Post by ant2ne on 2007-09-23
> **gnusci said:**
> I see you have all the necessary stuff to compile gtk code...


[http://www.gtk.org/tutorial/c39.html#SEC-HELLOWORLD](http://www.gtk.org/tutorial/c39.html#SEC-HELLOWORLD)
```
#include <gtk/gtk.h>


/* This is a callback function. The data arguments are ignored
 * in this example. More on callbacks below. */
static void hello( GtkWidget *widget,
                   gpointer   data )
{
    g_print ("Hello World\n");
}

static gboolean delete_event( GtkWidget *widget,
                              GdkEvent  *event,
                              gpointer   data )
{
    /* If you return FALSE in the "delete_event" signal handler,
     * GTK will emit the "destroy" signal. Returning TRUE means
     * you don't want the window to be destroyed.
     * This is useful for popping up 'are you sure you want to quit?'
     * type dialogs. */

    g_print ("delete event occurred\n");

    /* Change TRUE to FALSE and the main window will be destroyed with
     * a "delete_event". */

    return TRUE;
}

/* Another callback */
static void destroy( GtkWidget *widget,
                     gpointer   data )
{
    gtk_main_quit ();
}

int main( int   argc,
          char *argv[] )
{
    /* GtkWidget is the storage type for widgets */
    GtkWidget *window;
    GtkWidget *button;
    
    /* This is called in all GTK applications. Arguments are parsed
     * from the command line and are returned to the application. */
    gtk_init (&argc, &argv);
    
    /* create a new window */
    window = gtk_window_new (GTK_WINDOW_TOPLEVEL);
    
    /* When the window is given the "delete_event" signal (this is given
     * by the window manager, usually by the "close" option, or on the
     * titlebar), we ask it to call the delete_event () function
     * as defined above. The data passed to the callback
     * function is NULL and is ignored in the callback function. */
    g_signal_connect (G_OBJECT (window), "delete_event",
		      G_CALLBACK (delete_event), NULL);
    
    /* Here we connect the "destroy" event to a signal handler.  
     * This event occurs when we call gtk_widget_destroy() on the window,
     * or if we return FALSE in the "delete_event" callback. */
    g_signal_connect (G_OBJECT (window), "destroy",
		      G_CALLBACK (destroy), NULL);
    
    /* Sets the border width of the window. */
    gtk_container_set_border_width (GTK_CONTAINER (window), 10);
    
    /* Creates a new button with the label "Hello World". */
    button = gtk_button_new_with_label ("Hello World");
    
    /* When the button receives the "clicked" signal, it will call the
     * function hello() passing it NULL as its argument.  The hello()
     * function is defined above. */
    g_signal_connect (G_OBJECT (button), "clicked",
		      G_CALLBACK (hello), NULL);
    
    /* This will cause the window to be destroyed by calling
     * gtk_widget_destroy(window) when "clicked".  Again, the destroy
     * signal could come from here, or the window manager. */
    g_signal_connect_swapped (G_OBJECT (button), "clicked",
			      G_CALLBACK (gtk_widget_destroy),
                              G_OBJECT (window));
    
    /* This packs the button into the window (a gtk container). */
    gtk_container_add (GTK_CONTAINER (window), button);
    
    /* The final step is to display this newly created widget. */
    gtk_widget_show (button);
    
    /* and the window */
    gtk_widget_show (window);
    
    /* All GTK applications must have a gtk_main(). Control ends here
     * and waits for an event to occur (like a key press or
     * mouse event). */
    gtk_main ();
    
    return 0;
}
```

[http://www.gtk.org/tutorial/x111.html](http://www.gtk.org/tutorial/x111.html)
```
gcc -Wall -g helloworld.c -o helloworld `pkg-config --cflags gtk+-2.0` \
`pkg-config --libs gtk+-2.0`
```


```
antsvr@antubuntu:~/c$ gcc -Wall -g helloworld.c -o helloworld `pkg-config --cflags gtk+-2.0` \
>  `pkg-config --libs gtk+-2.0`
Package gtk+-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gtk+-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gtk+-2.0' found
Package gtk+-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gtk+-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gtk+-2.0' found
helloworld.c:1:21: error: gtk/gtk.h: No such file or directory
helloworld.c:5: error: expected ‘)’ before ‘*’ token
helloworld.c:11: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘delete_event’
helloworld.c:30: error: expected ‘)’ before ‘*’ token
helloworld.c: In function ‘main’:
helloworld.c:40: error: ‘GtkWidget’ undeclared (first use in this function)
helloworld.c:40: error: (Each undeclared identifier is reported only once
helloworld.c:40: error: for each function it appears in.)
helloworld.c:40: error: ‘window’ undeclared (first use in this function)
helloworld.c:41: error: ‘button’ undeclared (first use in this function)
helloworld.c:45: warning: implicit declaration of function ‘gtk_init’
helloworld.c:48: warning: implicit declaration of function ‘gtk_window_new’
helloworld.c:48: error: ‘GTK_WINDOW_TOPLEVEL’ undeclared (first use in this function)
helloworld.c:55: warning: implicit declaration of function ‘g_signal_connect’
helloworld.c:55: warning: implicit declaration of function ‘G_OBJECT’
helloworld.c:56: warning: implicit declaration of function ‘G_CALLBACK’
helloworld.c:56: error: ‘delete_event’ undeclared (first use in this function)
helloworld.c:56: error: ‘NULL’ undeclared (first use in this function)
helloworld.c:62: error: ‘destroy’ undeclared (first use in this function)
helloworld.c:65: warning: implicit declaration of function ‘gtk_container_set_border_width’
helloworld.c:65: warning: implicit declaration of function ‘GTK_CONTAINER’
helloworld.c:68: warning: implicit declaration of function ‘gtk_button_new_with_label’
helloworld.c:74: error: ‘hello’ undeclared (first use in this function)
helloworld.c:79: warning: implicit declaration of function ‘g_signal_connect_swapped’
helloworld.c:80: error: ‘gtk_widget_destroy’ undeclared (first use in this function)
helloworld.c:84: warning: implicit declaration of function ‘gtk_container_add’
helloworld.c:87: warning: implicit declaration of function ‘gtk_widget_show’
helloworld.c:95: warning: implicit declaration of function ‘gtk_main’
antsvr@antubuntu:~/c$ 
```:confused:


Learning this stuff would be a lot easier if it worked like claimed. :|

[WEB AS A LEARNING TOOL](*,)

If anyone would like to suggest a better tutorial to learn GTK I would love to hear it!!

---

