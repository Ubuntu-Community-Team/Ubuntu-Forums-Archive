---
title: "Set up probs' with Anjuta and GTK"
date: 2006-01-07
forum: Programming Talk
---

### Post by blastradius on 2006-01-07
HI

Newbie question.

I've installed Anjuta, gained a reasonable idea of C and C++ and decided
to have a look at GTK and SDL.  I've downloaded a basic example of SDL
and i've worked through the 'Starting off in Anjuta' tutorial.
Problem comes when i try to compile and i get a red strike through this
line;-      
#include <gtk/gtk.h>.  This causes errors throughout the program.

I get the same thing when i try to compile my SDL example and this
line:-
 #include <sdl/sdl.h>.  Same problem.

I've checked that GTK and SDL are installed on my system (Ubuntu Breezy)
and i don't know how to set Anjuta up to use these libs.

Please help.

Eric


P.S. Could someone explain the difference between SDL and STL, and what should i use to get into 2D graphics? (i did say i was a new coder!!)

Thanks

---

### Post by Hanj on 2006-01-07
Make sure you have the dev versions of GTK and SDL. If you already have, you should post the error messages you're getting (which is always a good idea when asking about compilation problems).

STL (Standard Template Library) is standard C++ library (i.e. you don't have to install it yourself, it comes with the compiler). It provides datastructures for linked lists and dynamic-size arrays.
SDL (Simple DirectMedia Layer) is a cross-platform library for 2D graphics.

---

### Post by blastradius on 2006-01-07
Thanks for the reply, i have got all the devs installed so here's the example GTK code:-

#include <gtk/gtk.h>
    ..
    ...
static gboolean delete_event( GtkWidget *widget,
                              GdkEvent  *event,
                              gpointer   data )
{
   return FALSE;
}

static void destroy( GtkWidget *widget,
                     gpointer   data )
{
    gtk_main_quit ();
}

int main( int   argc, char *argv[] )
{
    GtkWidget *window_Widget;
    ...
    ..

    gtk_init (&argc, &argv);

    //instantiate principal parent window

    window_Widget = gtk_window_new (GTK_WINDOW_TOPLEVEL);
    gtk_window_set_title (GTK_WINDOW (window_Widget), "Example GTK Skeleton");

    // Connect callbacks to main window

    g_signal_connect (G_OBJECT (window_Widget), "delete_event",
                      G_CALLBACK (delete_event), NULL);

    g_signal_connect (G_OBJECT (window_Widget), "destroy",
                      G_CALLBACK (destroy), NULL);

    gtk_container_set_border_width (GTK_CONTAINER (window_Widget), 10);

    // Call to container widget

    vBox_Widget = gtk_vbox_new (.......);  

    ...
    ..

    // Attach widgets to container widget.

    gtk_box_pack_start (GTK_BOX (vBox_Widget), new_component_1_Widget, TRUE, TRUE, 0);
    ...
    ..

    // Attach container to main window.

    gtk_container_add (GTK_CONTAINER (window_Widget), vBox_Widget);  

    ...
    ..

    gtk_widget_show (vBox_Widget);
    gtk_widget_show (window_Widget);

    gtk_main ();

    return 0;
}

If i run compile i get these errors:-

Compiling file: sdl_blit_sprite.cpp ...
g++       -c "sdl_blit_sprite.cpp" -o "sdl_blit_sprite.o"
sdl_blit_sprite.cpp:1:21: error: gtk/gtk.h: No such file or directory
sdl_blit_sprite.cpp:2: error: expected unqualified-id before &#8216;.&#8217; token
sdl_blit_sprite.cpp:11: error: variable or field &#8216;destroy&#8217; declared void
sdl_blit_sprite.cpp:11: error: &#8216;GtkWidget&#8217; was not declared in this scope
sdl_blit_sprite.cpp:11: error: &#8216;widget&#8217; was not declared in this scope
sdl_blit_sprite.cpp:12: error: &#8216;gpointer&#8217; was not declared in this scope
sdl_blit_sprite.cpp:12: error: initializer expression list treated as compound expression
sdl_blit_sprite.cpp:13: error: expected &#8216;,&#8217; or &#8216;;&#8217; before &#8216;{&#8217; token
sdl_blit_sprite.cpp: In function &#8216;int main(int, char**)&#8217;:
sdl_blit_sprite.cpp:19: error: &#8216;GtkWidget&#8217; was not declared in this scope
sdl_blit_sprite.cpp:19: error: &#8216;window_Widget&#8217; was not declared in this scope
sdl_blit_sprite.cpp:20: error: expected primary-expression before &#8216;...&#8217; token
sdl_blit_sprite.cpp:20: error: expected `;' before &#8216;...&#8217; token
sdl_blit_sprite.cpp:27: error: &#8216;GTK_WINDOW_TOPLEVEL&#8217; was not declared in this scope
sdl_blit_sprite.cpp:27: error: &#8216;gtk_window_new&#8217; was not declared in this scope
sdl_blit_sprite.cpp:28: error: &#8216;GTK_WINDOW&#8217; was not declared in this scope
sdl_blit_sprite.cpp:28: error: &#8216;gtk_window_set_title&#8217; was not declared in this scope
sdl_blit_sprite.cpp:32: error: &#8216;G_OBJECT&#8217; was not declared in this scope
sdl_blit_sprite.cpp:33: error: &#8216;delete_event&#8217; was not declared in this scope
sdl_blit_sprite.cpp:33: error: &#8216;G_CALLBACK&#8217; was not declared in this scope
sdl_blit_sprite.cpp:33: error: &#8216;NULL&#8217; was not declared in this scope
sdl_blit_sprite.cpp:33: error: &#8216;g_signal_connect&#8217; was not declared in this scope
sdl_blit_sprite.cpp:38: error: &#8216;GTK_CONTAINER&#8217; was not declared in this scope
sdl_blit_sprite.cpp:38: error: &#8216;gtk_container_set_border_width&#8217; was not declared in this scope
sdl_blit_sprite.cpp:42: error: &#8216;vBox_Widget&#8217; was not declared in this scope
sdl_blit_sprite.cpp:42: error: expected primary-expression before &#8216;...&#8217; token
sdl_blit_sprite.cpp:42: error: &#8216;gtk_vbox_new&#8217; was not declared in this scope
sdl_blit_sprite.cpp:44: error: expected primary-expression before &#8216;...&#8217; token
sdl_blit_sprite.cpp:44: error: expected `;' before &#8216;...&#8217; token
sdl_blit_sprite.cpp:50: error: expected primary-expression before &#8216;...&#8217; token
sdl_blit_sprite.cpp:50: error: expected `;' before &#8216;...&#8217; token
sdl_blit_sprite.cpp:57: error: expected primary-expression before &#8216;...&#8217; token
sdl_blit_sprite.cpp:57: error: expected `;' before &#8216;...&#8217; token
sdl_blit_sprite.cpp:61: error: &#8216;gtk_widget_show&#8217; was not declared in this scope
sdl_blit_sprite.cpp:63: error: &#8216;gtk_main&#8217; was not declared in this scope
Completed ... unsuccessful
Total time taken: 1 secs


I've probably gone over the top listing everything, but i wouldn't know what to leave out.

Thanks again for your help!

---

### Post by Hanj on 2006-01-07
Well, the code looks OK, but it seems the compiler can't find the gtk headers.  If you installed libgtk2.0-dev using apt-get you should have the file gtk.h in /usr/include/gtk-2.0/gtk. If the file isn't there you could try reinstalling the lib. If it is there, there might be something wrong with Anjuta's include path. Maybe someone with more experience on Anjuta can help you more.

---

### Post by blastradius on 2006-01-07
Hi 

The gtk file is there (2.0 + 2.4) so i guess it's Anjuta having problems finding the libs.

Thanks for your help.

---

### Post by Lews Therin on 2006-01-08
[QUOTE=blastradius]HI

Newbie question.

I've installed Anjuta, gained a reasonable idea of C and C++ and decided
to have a look at GTK and SDL.  I've downloaded a basic example of SDL
and i've worked through the 'Starting off in Anjuta' tutorial.
Problem comes when i try to compile and i get a red strike through this
line;-      
#include <gtk/gtk.h>.  This causes errors throughout the program.

I get the same thing when i try to compile my SDL example and this
line:-
 #include <sdl/sdl.h>.  Same problem.

I've checked that GTK and SDL are installed on my system (Ubuntu Breezy)
and i don't know how to set Anjuta up to use these libs.

Please help.

Eric


P.S. Could someone explain the difference between SDL and STL, and what should i use to get into 2D graphics? (i did say i was a new coder!!)

Thanks[/QUOTE]

Somewhere in Anjuta should be an option for compiler options and linker options. For GTK+, these are the options to use starting out. Include the backticks, they are needed.

Compiler: `pkg-config gtk+-2.0 --cflags`
Linker: `pkg-config gtk+-2.0 --libs`

---

### Post by blastradius on 2006-01-09
Thanks for your reply.

I've found - 'settings/compiler and linker options', within this there is an options tab (along with a few others like 'include paths' + library paths').  The options tab has fields for 'compiler flags + linker flags + additional libraries'.

Is it the fileds for flags i need to fill in? and do i need to enter anything in the other tabs?

Again, thanks for your help.

---

### Post by Lews Therin on 2006-01-09
[QUOTE=blastradius]Thanks for your reply.

I've found - 'settings/compiler and linker options', within this there is an options tab (along with a few others like 'include paths' + library paths').  The options tab has fields for 'compiler flags + linker flags + additional libraries'.

Is it the fileds for flags i need to fill in? and do i need to enter anything in the other tabs?

Again, thanks for your help.[/QUOTE]

Those look right. You only need to fill in compiler flags and linker flags as far as I know.

---

### Post by flerchjj on 2007-12-10
Try installing glib packages with the Synaptic Package manager.  This seemed to help resolve some similar errors for me.

---

### Post by jespdj on 2007-12-10
flerchjj, why did you respond to a thread that is almost two years old?

---

### Post by kuscsik on 2008-03-12
Probably he posted the answer because someone else (like me) may still have the same problem.

---

### Post by no_mosquitos on 2008-04-04
This manual have some info:

[http://www.anjuta.org/documents/C/anjuta-advanced-tutorial/index.html#simple-example-without-anjuta](http://www.anjuta.org/documents/C/anjuta-advanced-tutorial/index.html#simple-example-without-anjuta)

---

### Post by JBull on 2008-06-16
> **jespdj said:**
> flerchjj, why did you respond to a thread that is almost two years old?

Because it will help folks like me solve the same problem.

Thanks for the solution, flerchjj.  It worked.

---

