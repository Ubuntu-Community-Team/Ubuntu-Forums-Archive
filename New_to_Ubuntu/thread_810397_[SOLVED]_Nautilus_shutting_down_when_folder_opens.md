---
title: "[SOLVED] Nautilus shutting down when folder opens"
date: 2008-05-28
forum: New to Ubuntu
---

### Post by carloslosgrande on 2008-05-28
[FONT="Comic Sans MS"]Got a **weird** problem started today. Whenever I try to open a particular folder, the nautilus screen grays out and if I leave it for a while everything freezes. Have to restart.
I tried lots of my other folders - no trouble - just this one. It contains photos only.
I can force it to shutdown before it loops the whole system, but I only get about a minute or so, then its frozen.
I tried the older kernel - same deal. Tried total shutdown several times.
Any ideas?[/FONT]

---

### Post by quelx on 2008-05-28
Open a terminal window.

In that terminal window type ```
nautilus -c
``` and post the output then type ```
nautilus ~/
``` and if anything shows up in the terminal window, post that too.

---

### Post by carloslosgrande on 2008-05-28
[FONT="Comic Sans MS"]Hi quelx. Ok, here it is;[/FONT]
knot@home:~$ nautilus -c
running nautilus_self_check_file_utilities
running nautilus_self_check_file_operations
running nautilus_self_check_directory

(nautilus:9627): Gtk-WARNING **: Unable to locate theme engine in module_path: "experience",

(nautilus:9627): Gtk-WARNING **: Unable to locate theme engine in module_path: "experience",

(nautilus:9627): Gtk-WARNING **: Unable to locate theme engine in module_path: "experience",

(nautilus:9627): Gtk-WARNING **: Unable to locate theme engine in module_path: "experience",

(nautilus:9627): Gtk-WARNING **: Unable to locate theme engine in module_path: "experience",

(nautilus:9627): Gtk-WARNING **: Unable to locate theme engine in module_path: "experience",

(nautilus:9627): Gtk-WARNING **: Unable to locate theme engine in module_path: "experience",

(nautilus:9627): Gtk-WARNING **: Unable to locate theme engine in module_path: "experience",

(nautilus:9627): Gtk-WARNING **: Unable to locate theme engine in module_path: "experience",

(nautilus:9627): Gtk-WARNING **: Unable to locate theme engine in module_path: "experience",

(nautilus:9627): Gtk-WARNING **: Unable to locate theme engine in module_path: "experience",

(nautilus:9627): Gtk-WARNING **: Unable to locate theme engine in module_path: "experience",

(nautilus:9627): Gtk-WARNING **: Unable to locate theme engine in module_path: "experience",

(nautilus:9627): Gtk-WARNING **: Unable to locate theme engine in module_path: "experience",

(nautilus:9627): Gtk-WARNING **: Unable to locate theme engine in module_path: "experience",

(nautilus:9627): Gtk-WARNING **: Unable to locate theme engine in module_path: "experience",

(nautilus:9627): Gtk-WARNING **: Unable to locate theme engine in module_path: "experience",

(nautilus:9627): Gtk-WARNING **: Unable to locate theme engine in module_path: "experience",

(nautilus:9627): Gtk-WARNING **: Unable to locate theme engine in module_path: "experience",

(nautilus:9627): Gtk-WARNING **: Unable to locate theme engine in module_path: "experience",

(nautilus:9627): Gtk-WARNING **: Unable to locate theme engine in module_path: "experience",

(nautilus:9627): Gtk-WARNING **: Unable to locate theme engine in module_path: "experience",

(nautilus:9627): Gtk-WARNING **: Unable to locate theme engine in module_path: "experience",

(nautilus:9627): Gtk-WARNING **: Unable to locate theme engine in module_path: "experience",

(nautilus:9627): Gtk-WARNING **: Unable to locate theme engine in module_path: "experience",

(nautilus:9627): Gtk-WARNING **: Unable to locate theme engine in module_path: "experience",

(nautilus:9627): Gtk-WARNING **: Unable to locate theme engine in module_path: "experience",

(nautilus:9627): Gtk-WARNING **: Unable to locate theme engine in module_path: "experience",

(nautilus:9627): Gtk-WARNING **: Unable to locate theme engine in module_path: "experience",

(nautilus:9627): Gtk-WARNING **: Unable to locate theme engine in module_path: "experience",

(nautilus:9627): Gtk-WARNING **: Unable to locate theme engine in module_path: "experience",

(nautilus:9627): Gtk-WARNING **: Unable to locate theme engine in module_path: "experience",

(nautilus:9627): Gtk-WARNING **: Unable to locate theme engine in module_path: "experience",

(nautilus:9627): Gtk-WARNING **: Unable to locate theme engine in module_path: "experience",

(nautilus:9627): Gtk-WARNING **: Unable to locate theme engine in module_path: "experience",

(nautilus:9627): Gtk-WARNING **: Unable to locate theme engine in module_path: "experience",

(nautilus:9627): Gtk-WARNING **: Unable to locate theme engine in module_path: "experience",

(nautilus:9627): Gtk-WARNING **: Unable to locate theme engine in module_path: "experience",

(nautilus:9627): Gtk-WARNING **: Unable to locate theme engine in module_path: "experience",

(nautilus:9627): Gtk-WARNING **: Unable to locate theme engine in module_path: "experience",

(nautilus:9627): Gtk-WARNING **: Unable to locate theme engine in module_path: "experience",
/home/knot/.themes/eXperience - olive/gtk-2.0/gtkrc:332: Unable to find include file: "tweaks/file-list"
/home/knot/.themes/eXperience - olive/gtk-2.0/gtkrc:334: Unable to find include file: "tweaks/apply_styles"
/home/knot/.themes/eXperience - olive/gtk-2.0/gtkrc:343: error: invalid string constant "FileChooser", expected valid string constant
running nautilus_self_check_file
running nautilus_self_check_icon_container
running nautilus_self_check_file_utilities
running nautilus_self_check_file_operations
running nautilus_self_check_directory
running nautilus_self_check_file
running nautilus_self_check_icon_container
knot@home:~$ nautilus ~/

(nautilus:9636): Gtk-WARNING **: Unable to locate theme engine in module_path: "experience",

(nautilus:9636): Gtk-WARNING **: Unable to locate theme engine in module_path: "experience",

(nautilus:9636): Gtk-WARNING **: Unable to locate theme engine in module_path: "experience",

(nautilus:9636): Gtk-WARNING **: Unable to locate theme engine in module_path: "experience",

(nautilus:9636): Gtk-WARNING **: Unable to locate theme engine in module_path: "experience",

(nautilus:9636): Gtk-WARNING **: Unable to locate theme engine in module_path: "experience",

(nautilus:9636): Gtk-WARNING **: Unable to locate theme engine in module_path: "experience",

(nautilus:9636): Gtk-WARNING **: Unable to locate theme engine in module_path: "experience",

(nautilus:9636): Gtk-WARNING **: Unable to locate theme engine in module_path: "experience",

(nautilus:9636): Gtk-WARNING **: Unable to locate theme engine in module_path: "experience",

(nautilus:9636): Gtk-WARNING **: Unable to locate theme engine in module_path: "experience",

(nautilus:9636): Gtk-WARNING **: Unable to locate theme engine in module_path: "experience",

(nautilus:9636): Gtk-WARNING **: Unable to locate theme engine in module_path: "experience",

(nautilus:9636): Gtk-WARNING **: Unable to locate theme engine in module_path: "experience",

(nautilus:9636): Gtk-WARNING **: Unable to locate theme engine in module_path: "experience",

(nautilus:9636): Gtk-WARNING **: Unable to locate theme engine in module_path: "experience",

(nautilus:9636): Gtk-WARNING **: Unable to locate theme engine in module_path: "experience",

(nautilus:9636): Gtk-WARNING **: Unable to locate theme engine in module_path: "experience",

(nautilus:9636): Gtk-WARNING **: Unable to locate theme engine in module_path: "experience",

(nautilus:9636): Gtk-WARNING **: Unable to locate theme engine in module_path: "experience",

(nautilus:9636): Gtk-WARNING **: Unable to locate theme engine in module_path: "experience",

(nautilus:9636): Gtk-WARNING **: Unable to locate theme engine in module_path: "experience",

(nautilus:9636): Gtk-WARNING **: Unable to locate theme engine in module_path: "experience",

(nautilus:9636): Gtk-WARNING **: Unable to locate theme engine in module_path: "experience",

(nautilus:9636): Gtk-WARNING **: Unable to locate theme engine in module_path: "experience",

(nautilus:9636): Gtk-WARNING **: Unable to locate theme engine in module_path: "experience",

(nautilus:9636): Gtk-WARNING **: Unable to locate theme engine in module_path: "experience",

(nautilus:9636): Gtk-WARNING **: Unable to locate theme engine in module_path: "experience",

(nautilus:9636): Gtk-WARNING **: Unable to locate theme engine in module_path: "experience",

(nautilus:9636): Gtk-WARNING **: Unable to locate theme engine in module_path: "experience",

(nautilus:9636): Gtk-WARNING **: Unable to locate theme engine in module_path: "experience",

(nautilus:9636): Gtk-WARNING **: Unable to locate theme engine in module_path: "experience",

(nautilus:9636): Gtk-WARNING **: Unable to locate theme engine in module_path: "experience",

(nautilus:9636): Gtk-WARNING **: Unable to locate theme engine in module_path: "experience",

(nautilus:9636): Gtk-WARNING **: Unable to locate theme engine in module_path: "experience",

(nautilus:9636): Gtk-WARNING **: Unable to locate theme engine in module_path: "experience",

(nautilus:9636): Gtk-WARNING **: Unable to locate theme engine in module_path: "experience",

(nautilus:9636): Gtk-WARNING **: Unable to locate theme engine in module_path: "experience",

(nautilus:9636): Gtk-WARNING **: Unable to locate theme engine in module_path: "experience",

(nautilus:9636): Gtk-WARNING **: Unable to locate theme engine in module_path: "experience",

(nautilus:9636): Gtk-WARNING **: Unable to locate theme engine in module_path: "experience",
/home/knot/.themes/eXperience - olive/gtk-2.0/gtkrc:332: Unable to find include file: "tweaks/file-list"
/home/knot/.themes/eXperience - olive/gtk-2.0/gtkrc:334: Unable to find include file: "tweaks/apply_styles"
/home/knot/.themes/eXperience - olive/gtk-2.0/gtkrc:343: error: invalid string constant "FileChooser", expected valid string constant
[FONT="Comic Sans MS"]Checked theme 'experience' seems to be there.[/FONT]

---

### Post by wdaniels on 2008-05-28
> **carloslosgrande said:**
> Checked theme 'experience' seems to be there. The theme may be there but not the engine it needs (I've not heard of it before and can't see it in the repos so you will have to find and install that manually). But that is another problem - it shouldn't cause nautilus to close. My guess is that there is something causing it to lock up when it tries to render one of the photos for a thumbnail.

Try doing the same (nautilus <path>) where path is the particular folder in question, and see if you get an error message output to the terminal. You could also try disabling the thumbnail previews and see if it will open the folder then (in Nautilus set Preferences->Preview->Show Tumbnails=Never).

---

### Post by quelx on 2008-05-28
Try changin' the theme back to one of the default Ubuntu (just to see if it works)

Any one of these, Clearlooks/Crux/Glider, should suffice.

---

### Post by carloslosgrande on 2008-05-28
[FONT="Comic Sans MS"]Ok, clearlooks, glider and beastie work. crux and candybar don't.
I was using a custom theme.
this folder is only a little way down the dir tree, there are many more folders after it.
Thanks guys, any idea why this may have suddenly gone south?[/FONT]
[I]I just went and set it back to the original custom theme and checked that folder.....presto, it opened. I went down several of the dir trees until I got to actual photos - everything is fine.
wha????
The change must've kicked something in the guts.
Weird!
Thanks again guys.[/I]

---

