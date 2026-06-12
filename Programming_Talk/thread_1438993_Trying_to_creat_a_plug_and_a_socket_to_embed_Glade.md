---
title: "Trying to creat a plug and a socket to embed Glade into ValaIDE"
date: 2010-03-25
forum: Programming Talk
---

### Post by arkashkin on 2010-03-25
Hi,
I made the Glade application to create a plug, with a socket-id which it gets through a command argument.

From looking on this example:
(it is written in python but i'm programing in C..)

[COLOR="Sienna"]#!/usr/bin/python

import pygtk
pygtk.require('2.0')

import gtk,sys

Wid = 0L
if len(sys.argv) == 2:
    Wid = long(sys.argv[1])

plug = gtk.Plug(Wid)
print "Plug ID=", plug.get_id()

def embed_event(widget):
    print "I (",widget,") have just been embedded!"


plug.connect("embedded", embed_event)

entry = gtk.Entry()
entry.set_text("hello")
def entry_point(widget):
    print "You've changed my text to '%s'" % widget.get_text()


entry.connect("changed", entry_point)
plug.connect("destroy", gtk.mainquit)

plug.add(entry)
plug.show_all()

gtk.mainloop()[/COLOR]


, I understand plug is acting like a main a window ?? because the gtk.entry is inside it and there is no window created...
I know where in the code of Glade the main window is created.

This is how Glade's main function look like:
(in blue are my additions..)

[COLOR="Navy"]GtkWidget *plug;[/COLOR]
 GladeWindow *window;
......
......
gtk_init (NULL, NULL);
......
......
[COLOR="Navy"]int temp = atoi(argv[3]); //temp contains the socket-id
plug = gtk_plug_new (temp);[/COLOR] //plug is created and added to a socket..
window = GLADE_WINDOW (glade_window_new ());

[COLOR="Navy"]int winID = gtk_plug_get_id(plug);
printf("win_id of the plug is - %d  \n",winID);[/COLOR]

......
......
gtk_widget_show (GTK_WIDGET (window));
gtk_main ();
---------------------------------------------------
The plug is created and I'm able to connect it to a socket but nothing is changed (Glade's window doesn't embed into ValaIDE's...)

What I need to do besides calling - plug = gtk_plug_new (temp);
to properly create a plug so I could embed Glade into ValaIDE?

---

