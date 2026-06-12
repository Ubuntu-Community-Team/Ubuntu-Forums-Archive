---
title: "PyPe editor keeps closing"
date: 2005-10-08
forum: Programming Talk
---

### Post by richardq on 2005-10-08
I've installed the PyPe editor via Synaptic on Breezy and it just keeps closing as soon as I try to open an existing source file or even if I choose to create a new file, it just ends the program immediately. Any clues as to what the problem might be? I haven't found any threads identifying a similar problem. 

I'm a linux newbie and while maybe downloading the source and compiling might be an option, I wouldn't have a clue how to do that at the moment.. ;)


Richard

---

### Post by toojays on 2005-10-09
I'm not familiar with that program, but it sounds like it's crashing. You might be able to get it to give you a clue if you run it from a command line (i.e. run gnome-terminal, and run PyPe from there). Hopefully it will print something when it crashes. If it does, post it here.

---

### Post by richardq on 2005-10-09
Thanks for the suggestion, didn't think of that. Running it from the shell I get the following messages when I try to create a new source file or open an existing one:

richard@ubuntu:/usr/bin$ pype
[ Sun Oct  9 08:49:44 2005 ] Loading history from /home/richard/.pype/history.txt
[ Sun Oct  9 08:49:56 2005 ] found filetype-specific defaults python

(python:9959): Gtk-CRITICAL **: gtk_pixmap_new: assertion `val != NULL' failed

(python:9959): Gtk-CRITICAL **: gtk_box_pack_start: assertion `GTK_IS_WIDGET (child)' failed
Segmentation fault


Could I be using out of date libraries? No  clue.

---

### Post by toojays on 2005-10-10
Looks the a bug in that program to me.

---

### Post by UbuWu on 2005-10-10
Happens here as well. You should probably file a bug about it in malone.

Edit: did it for you: [https://launchpad.net/distros/ubuntu/+sources/pype/+bug/3028](https://launchpad.net/distros/ubuntu/+sources/pype/+bug/3028)

---

### Post by richardq on 2005-10-11
> Edit: did it for you:

Thank you.

Richard

---

### Post by subtler on 2006-04-20
the program does the same for me. I would assume it is a bug.

---

