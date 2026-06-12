---
title: "[SOLVED] Glade/GTK very beginners question"
date: 2008-04-22
forum: New to Ubuntu
---

### Post by anewguy on 2008-04-22
I have been following one of the online tutorials for using Glade and GTK.  In the very first sample program (it only creates a window and destroys it when the box is clicked) it has the following lines:

/*
To compile, use this command (those are backticks, not single quotes):
gcc -Wall -g -o tutorial main.c `pkg-config --cflags --libs gtk+-2.0 libglade-2.0`
*/


As far as I can tell, I think I have GTK installed, but when I run the above gcc (changed to match my source name) I get the following:

dave@dave-desktop:~/cvsutil/src$ gcc -Wall -g -o cvsutil cvsutilgtk.c `pkg-config --cflags --libs gtk+-2.0 libglade-2.0`
Package gtk+-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gtk+-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gtk+-2.0' found
Package libglade-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `libglade-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libglade-2.0' found
cvsutilgtk.c:5:21: error: gtk/gtk.h: No such file or directory
cvsutilgtk.c:6:25: error: glade/glade.h: No such file or directory
cvsutilgtk.c: In function &#8216;main&#8217;:
cvsutilgtk.c:11: error: &#8216;GladeXML&#8217; undeclared (first use in this function)
cvsutilgtk.c:11: error: (Each undeclared identifier is reported only once
cvsutilgtk.c:11: error: for each function it appears in.)
cvsutilgtk.c:11: error: &#8216;gxml&#8217; undeclared (first use in this function)
cvsutilgtk.c:12: error: &#8216;GtkWidget&#8217; undeclared (first use in this function)
cvsutilgtk.c:12: error: &#8216;window&#8217; undeclared (first use in this function)
cvsutilgtk.c:14: warning: implicit declaration of function &#8216;gtk_init&#8217;
cvsutilgtk.c:16: warning: implicit declaration of function &#8216;glade_xml_new&#8217;
cvsutilgtk.c:16: error: &#8216;NULL&#8217; undeclared (first use in this function)
cvsutilgtk.c:17: warning: implicit declaration of function &#8216;glade_xml_get_widget&#8217;
cvsutilgtk.c:18: warning: implicit declaration of function &#8216;glade_xml_signal_connect&#8217;
cvsutilgtk.c:19: warning: implicit declaration of function &#8216;G_CALLBACK&#8217;
cvsutilgtk.c:19: error: &#8216;gtk_main_quit&#8217; undeclared (first use in this function)
cvsutilgtk.c:21: warning: implicit declaration of function &#8216;g_object_unref&#8217;
cvsutilgtk.c:21: warning: implicit declaration of function &#8216;G_OBJECT&#8217;
cvsutilgtk.c:23: warning: implicit declaration of function &#8216;gtk_widget_show&#8217;
cvsutilgtk.c:24: warning: implicit declaration of function &#8216;gtk_main&#8217;
dave@dave-desktop:~/cvsutil/src$ 

I know after it not finding the gtk package that everything else is a result of that.

What should a beginner like me do?

Thanks!  :)

EDIT:  Forgot to mention that glade and gtk seem to be installed in /usr/lib if that helps any.

---

### Post by tonyr1988 on 2008-04-22
I haven't messed with GTK much, but I believe you'll need the libgtk2.0-dev package in Synaptic, or:

> sudo apt-get install libgtk2.0-dev

---

### Post by anewguy on 2008-04-22
Tried what you suggested - it installed some stuff, but the compile still fails just the same.

I tried changing the gcc line by removing the PKG_CONFIG_PATH and just putting -l in front of each library name as I have done in the past:

 gcc -Wall -g -o cvsutil cvsutilgtk.c  -lgtk+-2.0 -llibglade-2.0


The results are slightly changed, but I still can't figure out what is wrong (like WHERE is looking for the /glade and /gtk directories??):

dave@dave-desktop:~/cvsutil/src$ gcc -Wall -g -o cvsutil cvsutilgtk.c  -lgtk+-2.0 -llibglade-2.0
cvsutilgtk.c:5:21: error: gtk/gtk.h: No such file or directory
cvsutilgtk.c:6:25: error: glade/glade.h: No such file or directory

Followed of course by a lot of "not declared" type errors.

I'm really quite confused here.  Any help would be appreciated!! :(

---

### Post by anewguy on 2008-04-22
Fixed those errors by uninstalling glade and installing glade-gnome packages.

Thanks for the help!  :)

---

