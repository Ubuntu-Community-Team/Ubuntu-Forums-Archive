---
title: "Cannot open gedit by double clicking a text file or through terminal."
date: 2014-10-02
forum: New to Ubuntu
---

### Post by rjochacko on 2014-10-02
Cannot open gedit by double clicking a text file or through terminal.

  gedit in terminal shows the following error:    

:confused:
  [I](gedit:3247): Gtk-WARNING **: Theme parsing error: gtk-main.css:43:30: Failed to import: Error opening file: No such file or directory

(gedit:3247): GLib-GIO-ERROR **: Settings schema 'org.gnome.gedit.preferences.editor' is not installed

Trace/breakpoint trap (core dumped).  
:confused:

[/I]In '/var/crash' it showing:  
 "gedit crashed with signal 5 in g_object_new_valist()".

   I tried reinstalling gedit.:mad: I am using gedit 3.10.4 in ubuntu 14.04.

  Can anyone help?

---

### Post by vasa1 on 2014-10-02
> **rjochacko said:**
> ...

  *(gedit:3247): Gtk-WARNING **: Theme parsing error: gtk-main.css:43:30: Failed to import: Error opening file: No such file or directory...*...
Did you install a new theme or change themes?
Was gedit ever working for you or did the problem start recently?

---

### Post by rjochacko on 2014-10-02
I didn't install any themes. But recently there was a problem with shortcuts (Ctrl+A and Ctrl+F) in gedit.So I installed 'gnome-tweak-tool' and changed keybinding themes from 'Emacs' to 'Default', that could solve the problem with shortcuts. And the new problem started recently. I tried undoing the key theme, but no result.

---

### Post by rjochacko on 2014-10-02
One more observation:
I tried changing theme to 'High Contrast' (Default was 'Ambience') from System setting->Appearance. And now the first error message ("*(gedit:3247): Gtk-WARNING **: Theme parsing error:  gtk-main.css:43:30: Failed to import: Error opening file: No such file  or directory*") has gone, but the rest exists and no result too.

---

### Post by rjochacko on 2014-10-03
PROBLEM SOLVED!!!!!

Tried with  "dpkg -S org.gtk.Settings" on terminal and the result was:

dpkg-query: warning: files list file for package 'gedit-common' missing; assuming package has no files currently installed
libgtk-3-common: /usr/share/glib-2.0/schemas/org.gtk.Settings.FileChooser.gschema.xml
libgtk-3-common: /usr/share/glib-2.0/schemas/org.gtk.Settings.ColorChooser.gschema.xml

So I reinstalled 'gedit-common' alone using synaptic, thats all problem solved.
I don't know what exaactly has happened, but could get rid of that.

Thank you all ubuntuforum members.

---

