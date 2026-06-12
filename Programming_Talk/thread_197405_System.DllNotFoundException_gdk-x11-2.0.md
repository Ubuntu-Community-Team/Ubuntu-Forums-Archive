---
title: "System.DllNotFoundException: gdk-x11-2.0"
date: 2006-06-15
forum: Programming Talk
---

### Post by traherom on 2006-06-15
While attempting to use the [TrayLib.cs](http://www.mono-project.com/GtkSharpNotificationIcon) code from the Mono website, I encounter this error when I attempt to run the project I'm working on:
> Unhandled Exception: System.DllNotFoundException: gdk-x11-2.0
in (wrapper managed-to-native) Egg.TrayIcon:gdk_x11_display_get_xdisplay (intptr)
in [0x00018] (at /home/ryan/src/rbr/traylib.cs:35) Egg.TrayIcon:OnRealized ()
in <0x00036> Gtk.Widget:realized_cb (IntPtr widget)
in (wrapper native-to-managed) Gtk.Widget:realized_cb (intptr)
in <0x00000> <unknown method>
in (wrapper managed-to-native) Gtk.Widget:gtk_widget_show_all (intptr)
in <0x00017> Gtk.Widget:ShowAll ()
in [0x0004d] (at /home/ryan/src/rbr/Main.cs:35) rbr.MainClass:.ctor ()
in [0x00005] (at /home/ryan/src/rbr/Main.cs:16) rbr.MainClass:Main (System.String[] args)

The same thing occurs when I try to run the code the author of that page provided there as is, as well as when I gave the wallpaper changer found [here](http://ubuntuforums.org/showthread.php?t=49336&page=5) a try. (I noticed the changer while searching for this same problem. At least one other person reported the exact same error in that thread.)

A quick locate shows me that the library is at /usr/lib/libgdk-x11-2.0.so.0, so I don't think I need to install anything... for some reason mono just doesn't see it.

I'm new to mono... any ideas on what the problem is?

---

