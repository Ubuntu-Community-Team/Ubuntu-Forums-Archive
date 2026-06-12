---
title: "Can't get gtk hello world to work :)"
date: 2005-11-13
forum: Programming Talk
---

### Post by idn on 2005-11-13
I want to start developing in gnome, so I installed everything I think I needd, but when I go to compile the following 
```
#include <gtk/gtk.h>

int main( int   argc,
          char *argv[] )
{
    GtkWidget *window;
    
    gtk_init (&argc, &argv);
    
    window = gtk_window_new (GTK_WINDOW_TOPLEVEL);
    gtk_widget_show  (window);
    
    gtk_main ();
    
    return 0;
}

```

I get the following erros in Anjuta

```
error: gtk/gtk.h no such file or directory
```

Does anyone know what I am doing wrong?

---

### Post by nszabolcs on 2005-11-13
did you installed gtk development packages? (libgtk2.0-dev)

---

### Post by idn on 2005-11-13
Yeah I have it installed, I dont know why it isnt working

---

### Post by pdpi on 2005-11-13
hmmm

I tried compiling that source on my system. No go either, but I hadn't installed libgtk2.0-dev. After installing it, still no go. I don't have a gtk directory in /usr/include, but I do have a gtk-2.0 one. I tried making /usr/include/gtk a symlink to  /usr/include/gtk-2.0/gtk, which made the output of gcc hello-gtk.c turn into 4466 (yes, almost fourty five hundred) lines of errors. So I can't come up with any more suggestions...

---

### Post by dogen on 2005-11-13
What's the default gcc include and library path? 

Does it use a system path, and if so, did you specify it in your '.bash_profile' ? 

Is there a default location - like '/usr/local/lib'? Are your gtk files there?

Did you try specifying the exact location in the command line with -I?

e.g. 
$ gcc -Wall -I/opt/gdbm-1.8.3/include dbmain.c

And you have to ask, if you're using an IDE like Anjuta, if that part of the equation is getting in the way.

---

### Post by vgeddes on 2005-11-14
Try using the commandline instead of anjuta, you will get to the root of the error quickly. I find that high-level IDE's  _sometimes_ make life more complicated.

this command will compile your code, and link it with gtk:

$ gcc main.c -o main `pkg-config --cflags --libs gtk+-2.0`

---

