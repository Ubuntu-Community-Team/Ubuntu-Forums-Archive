---
title: "Rhythmbox crash"
date: 2013-03-08
forum: New to Ubuntu
---

### Post by Applesauce on 2013-03-08
When I opened Rhythmbox Player it looked ok for about half a second before crashing. I tried opening it from a terminal with the same result. Here is the info that showed up in the terminal.

**elam@Compaq-Presario-CQ60:~$ rhythmbox**

**(rhythmbox:2035): Rhythmbox-WARNING **: Unable to grab media player keys: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SettingsDaemon was not provided by any .service files**
**WARNING: gnome-keyring:: couldn't connect to: /tmp/keyring-GfA8yQ/pkcs11: No such file or directory**


Does this help? Any other info needed?

---

### Post by cortman on 2013-03-08
Try running

```
sudo apt-get install gstreamer-dbus-media-service
```[COLOR=#333333][FONT=Lucida Grande]

[/FONT][/COLOR]and see if that fixes it.
I would also look into Audacious for that lower-end system if I were you. :P

---

### Post by Applesauce on 2013-03-08
Tried it. Just discovered a new trick for the crash. It will run fine, but if I put in a cd with .wav tracks, it will crash as soon as it gets started. 

This time it spit out this.


**elam@Compaq-Presario-CQ60:~$ rhythmbox**

**(rhythmbox:2547): Gtk-CRITICAL **: gtk_builder_get_object: assertion `GTK_IS_BUILDER (builder)' failed**

**(rhythmbox:2547): Gtk-CRITICAL **: gtk_builder_get_object: assertion `GTK_IS_BUILDER (builder)' failed**

**(rhythmbox:2547): Gtk-CRITICAL **: gtk_widget_set_sensitive: assertion `GTK_IS_WIDGET (widget)' failed**

**(rhythmbox:2547): Gtk-CRITICAL **: gtk_widget_set_sensitive: assertion `GTK_IS_WIDGET (widget)' failed**

**(rhythmbox:2547): Rhythmbox-WARNING **: Unable to grab media player keys: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SettingsDaemon was not provided by any .service files**
**WARNING: gnome-keyring:: couldn't connect to: /tmp/keyring-GfA8yQ/pkcs11: No such file or directory**

---

### Post by Applesauce on 2013-03-11
Putting the cd in while Rhythmbox is up and running will cause it to crash. I tried sudo apt-get install rhythmbox --reinstall at the advice of cortman, but that didn't solve it.

---

### Post by Pufftones on 2013-03-19
I am having a very similar issue to the one that you are having.  I originally thought that my problem was related to Rhythmbox updating to a version from an unstable source by the Webupd8Team, I added that source because it allowed me to install the PPA for accessing the file system on my android phone.  Anyway, I reinstalled and forced the regular Ubuntu version in Synaptic, double checked and it definitely is not the Webupd8Team version and it still crashes.  When I launch it from the Terminal, I get about a zillion messages that all read something like



(rhythmbox:12590): Gtk-WARNING **: Theme directory mimetypes/96 of theme malys-uniblue has no size field




(rhythmbox:12590): Gtk-WARNING **: Theme directory places/96 of theme malys-uniblue has no size field




(rhythmbox:12590): Gtk-WARNING **: Theme directory status/96 of theme malys-uniblue has no size field




(rhythmbox:12590): Gtk-WARNING **: Theme directory stock/96 of theme malys-uniblue has no size field

then once the program has loaded my entire music library it crashes and the Terminal spits out this 

(rhythmbox:12590): Rhythmbox-WARNING **: Could not open device /dev/radio0
**
RhythmDB:ERROR:rhythmdb-tree.c:1517:remove_child: assertion failed: (g_hash_table_remove (parent->children, data))
Unable to open ~/.mtpz-data for reading, MTPZ disabled.Aborted (core dumped)

What seems most odd is that the Terminal is clearly making some kind of fuss about the contents of malys-uniblue which is my system icons set.  If someone could please help me, that would be great, thanks.

---

