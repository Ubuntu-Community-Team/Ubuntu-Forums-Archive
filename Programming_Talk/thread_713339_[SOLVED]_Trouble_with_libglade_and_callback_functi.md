---
title: "[SOLVED] Trouble with libglade and callback functions"
date: 2008-03-02
forum: Programming Talk
---

### Post by derrick81787 on 2008-03-02
Hello everyone,

I'm pretty new to using libglade and GTK, and I'm having trouble setting up my callback functions.  I've defined various signals and their callbacks using Glade Interface Designer, and then I made a separate callbacks.h and callbacks.c with those functions in them.  When I load my xml file and use glade_xml_auto_connect(), I get the following warnings printed to the terminal.

```
(ddimage:15086): libglade-WARNING **: could not find signal handler 'backupDevice'.

(ddimage:15086): libglade-WARNING **: could not find signal handler 'quitProgram'.

(ddimage:15086): libglade-WARNING **: could not find signal handler 'restoreDevice'.

(ddimage:15086): libglade-WARNING **: could not find signal handler 'showAboutDialog'.

(ddimage:15086): libglade-WARNING **: could not find signal handler 'refreshDevices'.

```

The xml file is getting loaded correctly because the main window displays like it should.  I have the functions declared in callbacks.h and defined in callbacks.c.  Here is a sample definition of one of my functions (they all look the same right now):

```
void showAboutDialog(GtkWidget* widget, gpointer data)
{  
   printf("This should show the about dialog\n");
}
```

Can someone please let me know what I'm doing wrong? I've been looking at this for quite a while now, and I just can't figure out why it's not working.  I'm programming in C by the way, just in case you weren't sure.

Thanks a lot,
Derrick

*****Edit:**
Also, here's my main function located in main.c, just in case it's of any help to anyone:

```
#include <gtk/gtk.h>
#include <glade/glade.h>
#include "callbacks.h"

int main(int argc, char** argv)
{
   // initialize gtk
   gtk_init(&argc, &argv);

   // get the .glade file for the interface
   GladeXML* xml;
   xml = glade_xml_new("interface.glade", NULL, NULL);
   
   // connect the signal handlers
   glade_xml_signal_autoconnect(xml);

   // run the main loop
   gtk_main();

   return 0;
}
```

---

### Post by derrick81787 on 2008-03-04
Any ideas anyone?  Does it look like I'm doing everything alright?

---

### Post by RJ8722 on 2008-03-04
I'm not sure but my guess is you need to compile with the flag -rdynamic.

---

### Post by derrick81787 on 2008-03-04
I solved the problem.  After searching some more, I added the line "ddimage_LDFLAGS = -export-dynamic" to my Makefile.am, and then ran configure and make again.  I don't know why i couldn't find this the other day, but this fixed the problem.

Anyway, I'm going to mark this thread as solved, and hopefully it'll help someone.  By the way, if you're trying this yourself, replace 'ddimage' with the name of your binary.

See ya,
Derrick

---

### Post by derrick81787 on 2008-03-04
> I'm not sure but my guess is you need to compile with the flag -rdynamic.
Thanks a lot.  I think that would've worked too, but I didn't see the post until after I already solved the problem.  I appreciate the reply though.  Do you know what the difference is between -rdynamic and -export-dynamic?

Derrick

---

### Post by night_fox on 2009-03-04
Hi, I have the same problem and I'm using a normal makefile. I've tried calling gcc with "--export-dynamic" and "-rdynamic" but it wont work.

How do I force gcc to export my function as it's correct name? I've tried disassembling it with lida and most function names come out as gobbledegook and my callback function doesn't get mentioned! Even with a very simple program.

---

