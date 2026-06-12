---
title: "flash wont work when somethings downloading"
date: 2008-09-15
forum: New to Ubuntu
---

### Post by tjwoosta on 2008-09-15
so i have been away from my computer for a while and just got back online

the first thing i noticed since i have been back online is that flash will no longer work when i am downloading things

it works fine if i open firefox and go straight to a flash video

but if i download something (anything at all, like a free game or something) then i try youtube i just get a blank space where the video should be

so basically i need to wait for the download to finish, then close and reopen firefox before i can watch flash videos

why is this hapening?

this never used to happen 

was there a recent flash update within the past month or so?

---

### Post by MaindotC on 2008-09-15
Launch FF3 from the terminal, start a download, and then open a youtube video.  Post the output from the terminal.

---

### Post by Crafty Kisses on 2008-09-15
It could be a conflict with Firefox or Flash, or in this case probably both. Is it when ANYTHING is downloading or only somethings.

---

### Post by tjwoosta on 2008-09-15
it appears to be happening whenever i download anything at all

here is the oputput of the terminal after downloading something and trying to play a youtube video

```

tj@tj-laptop:~$ firefox
GCJ PLUGIN: thread 0x622940: NP_GetMIMEDescription
GCJ PLUGIN: thread 0x622940: NP_GetMIMEDescription return
GCJ PLUGIN: thread 0x622940: NP_GetValue
GCJ PLUGIN: thread 0x622940: NP_GetValue: returning plugin name.
GCJ PLUGIN: thread 0x622940: NP_GetValue return
GCJ PLUGIN: thread 0x622940: NP_GetValue
GCJ PLUGIN: thread 0x622940: NP_GetValue: returning plugin description.
GCJ PLUGIN: thread 0x622940: NP_GetValue return

(npviewer.bin:14407): Gtk-CRITICAL **: gtk_style_detach: assertion `style->attach_count > 0' failed

(npviewer.bin:14407): Gtk-CRITICAL **: gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed

(npviewer.bin:14407): Gtk-CRITICAL **: gtk_widget_destroy: assertion `GTK_IS_WIDGET (widget)' failed

(npviewer.bin:14407): Gtk-CRITICAL **: gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed

(npviewer.bin:14407): Gtk-CRITICAL **: gtk_widget_destroy: assertion `GTK_IS_WIDGET (widget)' failed

(npviewer.bin:14407): Gtk-CRITICAL **: gtk_widget_destroy: assertion `GTK_IS_WIDGET (widget)' failed



```

this part shows up imediatly after starting firefox
```

GCJ PLUGIN: thread 0x622940: NP_GetMIMEDescription
GCJ PLUGIN: thread 0x622940: NP_GetMIMEDescription return
GCJ PLUGIN: thread 0x622940: NP_GetValue
GCJ PLUGIN: thread 0x622940: NP_GetValue: returning plugin name.
GCJ PLUGIN: thread 0x622940: NP_GetValue return
GCJ PLUGIN: thread 0x622940: NP_GetValue
GCJ PLUGIN: thread 0x622940: NP_GetValue: returning plugin description.
GCJ PLUGIN: thread 0x622940: NP_GetValue return

```

nothing shows up when i download the file

then this part shows up after tyring to play the video

```

(npviewer.bin:14407): Gtk-CRITICAL **: gtk_style_detach: assertion `style->attach_count > 0' failed

(npviewer.bin:14407): Gtk-CRITICAL **: gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed

(npviewer.bin:14407): Gtk-CRITICAL **: gtk_widget_destroy: assertion `GTK_IS_WIDGET (widget)' failed

(npviewer.bin:14407): Gtk-CRITICAL **: gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed

(npviewer.bin:14407): Gtk-CRITICAL **: gtk_widget_destroy: assertion `GTK_IS_WIDGET (widget)' failed

(npviewer.bin:14407): Gtk-CRITICAL **: gtk_widget_destroy: assertion `GTK_IS_WIDGET (widget)' failed


```

---

### Post by kansasnoob on 2008-09-16
Check out Post #7 here:

[http://ubuntuforums.org/showthread.php?t=919695](http://ubuntuforums.org/showthread.php?t=919695)

---

