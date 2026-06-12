---
title: "GDB and gtk_main () - problm"
date: 2006-07-24
forum: Programming Talk
---

### Post by tomcio on 2006-07-24
Hi!

I'm quite new to GDB and I have stupid problem. I know how to debug console applications, but I have problems with debuging GUI application. There is no problem, but when program execute main loop function like gtk_main () I'm not able to do enything with GDB!

After the program enter to the main loop I can't execute any command in gdb's console, while debuged program won't be finished. It's very strange...

How can I get a backtrace from GUI (for me GTK+) application?

---

### Post by xtacocorex on 2006-07-24
I did a quick google search for "debugging backtrace for GTK+ apps" (without the quotes and found the following information from the first link.

> Be sure you compile your program with the -g (or -ggdb) gcc flag on and WITHOUT the "-fomit-frame-pointer" parameter.
> Run your app in a debugger with the --sync option, and when it crashes with the error the backtrace will accurately reflect the function that caused the error.
> Put a breakpoint on main
then run the program until it stops (almost instantly :)
then put a breakpoint on gdk_x_error
then continue like so
b main<enter>
run --sync<enter>
b gdk_x_error<enter>
cont<enter>
then play with your program until you get to the error and gdb will stop
and if you do a backtrace it should give you the place of the error.

Here is the link to the webpage: [http://mail.gnome.org/archives/gtk-app-devel-list/2000-November/msg00218.html](http://mail.gnome.org/archives/gtk-app-devel-list/2000-November/msg00218.html)

I hope this helps some as I've never used GDB.

---

