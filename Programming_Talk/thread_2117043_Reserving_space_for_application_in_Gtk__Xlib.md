---
title: "Reserving space for application in Gtk / Xlib"
date: 2013-02-17
forum: Programming Talk
---

### Post by Virtuality314 on 2013-02-17
Hello,

I was trying to create an application in Gtk and C++ which is basically a panel. What I want to do is reserve space on the screen so it can always be displayed. After some Googling, I got results telling me I needed to use Xlib, and the XChangeProperty function.

I tried doing this, but I got extremely confused on what to do. The docs of Xlib didn't help me much. I also realised that LxPanel does this, but I couldn't understand the code very much.

I would love it if someone could help me on this,

Thanks in advance.

---

### Post by SledgeHammer_999 on 2013-02-17
I think you need to create a Gtk::Window with WINDOWS_POPUP as windowtype.

---

### Post by Virtuality314 on 2013-02-18
Setting type as GTK_POPUP didn't work.

You can do it easily in python, as described in [this]("http://stackoverflow.com/questions/5949230/python-tell-x-to-reserve-screen-space-for-application") post, but I am looking for a way to do this in C++.

EDIT: I have managed to get this:

```

gdk_property_change (gdk_window , net_wm_strut_atom, cardinal_atom, 32, GDK_PROP_MODE_REPLACE, (guchar *) &strut, 4);

```

But I have no idea what 'strut' is meant to represent. In the docs, it is labelled as "data" but I don't know how to declare it or anything. :( I probably will learn Xlib / GDK in the future, but I just need someone to maybe help me with that function. Double EDIT: please

---

### Post by Virtuality314 on 2013-02-18
Ok, so I think I am finally getting somewhere. Here is my current code:

```

#include <gtk/gtk.h>
#include <X11/Xlib.h>

int main (int argc, char *argv[])
{
	GtkWidget *window;
	
	gtk_init (&argc, &argv);
	
	window = gtk_window_new (GTK_WINDOW_TOPLEVEL);
	gtk_window_set_default_size (GTK_WINDOW (window), 1440, 24);
	gtk_window_set_gravity (GTK_WINDOW (window), GDK_GRAVITY_NORTH);
	gtk_window_move (GTK_WINDOW (window), 0, 0);
	gtk_window_set_decorated (GTK_WINDOW (window), FALSE);
	gtk_window_set_type_hint(GTK_WINDOW (window), GDK_WINDOW_TYPE_HINT_DOCK);
	
	static GdkAtom net_wm_strut_atom = 0;
	static GdkAtom cardinal_atom = 0;
	net_wm_strut_atom = gdk_atom_intern_static_string ("_NET_WM_STRUT");
	cardinal_atom = gdk_atom_intern_static_string ("CARDINAL");	 
	
	GdkWindow *gdk_window = gtk_widget_get_window(GTK_WIDGET(window));
	
	gulong strut_data [4] = {0, 0 ,0, 0};
	
	gdk_property_change (gdk_window , net_wm_strut_atom, cardinal_atom, 32, GDK_PROP_MODE_REPLACE, (guchar*) &strut_data, 4);
	
	g_signal_connect (window, "destroy", G_CALLBACK (gtk_main_quit), NULL);
	
	gtk_widget_show (window);
	
	gtk_main ();
	
	return 0;
}


```

The problem I am having now is that gdk_property_change is causing a segmentation fault. I suspect that this may be because of strut_data.

Here is my output from gdb:

> 
(no debugging symbols found)
Starting program: /home/xylon/Dev/Panel/panel 
[Thread debugging using libthread_db enabled]
Using host libthread_db library "/lib/x86_64-linux-gnu/libthread_db.so.1".
[New Thread 0x7ffff04a0700 (LWP 5175)]
[New Thread 0x7fffefc9f700 (LWP 5176)]

(panel:5174): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:66:21: Junk at end of value

(panel:5174): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:120:43: Invalid animation description

(panel:5174): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:125:23: Horizontal and vertical offsets are required

(panel:5174): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:132:23: Horizontal and vertical offsets are required

(panel:5174): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:141:23: Horizontal and vertical offsets are required

(panel:5174): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:149:23: Horizontal and vertical offsets are required

(panel:5174): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:156:23: Horizontal and vertical offsets are required

(panel:5174): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:170:23: Horizontal and vertical offsets are required

(panel:5174): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:177:23: Horizontal and vertical offsets are required

(panel:5174): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:184:23: Horizontal and vertical offsets are required

(panel:5174): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:1463:0: unknown @ rule

(panel:5174): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:1548:97: 'currentColor' is not a valid color name

(panel:5174): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:1556:32: Junk at end of value

(panel:5174): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:1568:13: 'animation' is not a valid property name

(panel:5174): Gtk-WARNING **: Theme parsing error: gnome-applications.css:98:18: Horizontal and vertical offsets are required

(panel:5174): Gtk-WARNING **: Theme parsing error: gnome-applications.css:162:39: Missing closing bracket for pseudo-class

(panel:5174): Gtk-WARNING **: Theme parsing error: granite-widgets.css:159:28: 'px' is not a valid color name

Program received signal SIGSEGV, Segmentation fault.
0x00007ffff750b970 in gdk_property_change () from /usr/lib/x86_64-linux-gnu/libgdk-3.so.0


This is getting confusing now...I've seen this being implemented about 6 times in separate applications now, but it isn't working for me.

---

### Post by Linteg on 2013-02-19
> **Virtuality314 said:**
> Ok, so I think I am finally getting somewhere. Here is my current code:

```

gulong strut_data [4] = {0, 0 ,0, 0};
gdk_property_change (gdk_window , net_wm_strut_atom, cardinal_atom, 32, GDK_PROP_MODE_REPLACE, (guchar*) &strut_data, 4);

```
The problem I am having now is that gdk_property_change is causing a segmentation fault. I suspect that this may be because of strut_data.

Are you sure you want to pass strut_data as a  *gulong *** casted to a *guchar **? I would try
```
gdk_property_change (gdk_window , net_wm_strut_atom, cardinal_atom, 32, GDK_PROP_MODE_REPLACE, (guchar*) strut_data, 4);
```

---

### Post by Virtuality314 on 2013-02-20
It still produces a segmentation fault after removing the '&'.

I wonder if it would be better to just fork another panel...

---

