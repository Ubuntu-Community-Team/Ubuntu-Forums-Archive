---
title: "Asus N61Jv webcam won't start"
date: 2012-02-02
forum: New to Ubuntu
---

### Post by Highstaker on 2012-02-02
Greetings, people.

My built-in webcam won't work. Cheese shows black screen.
Here is what it says when i launch Cheese:
> (cheese:3700): Gtk-WARNING **: Attempting to add a widget with type GtkImage to a GtkToggleButton, but as a GtkBin subclass a GtkToggleButton can only contain one widget at a time; it already contains a widget of type GtkLabel

(cheese:3700): Gtk-WARNING **: Attempting to add a widget with type GtkImage to a GtkToggleButton, but as a GtkBin subclass a GtkToggleButton can only contain one widget at a time; it already contains a widget of type GtkLabel

(cheese:3700): Gtk-WARNING **: Attempting to add a widget with type GtkImage to a GtkToggleButton, but as a GtkBin subclass a GtkToggleButton can only contain one widget at a time; it already contains a widget of type GtkLabel

(cheese:3700): Gtk-WARNING **: Attempting to add a widget with type GtkHBox to a GtkButton, but as a GtkBin subclass a GtkButton can only contain one widget at a time; it already contains a widget of type GtkLabel

(cheese:3700): Gtk-WARNING **: Attempting to add a widget with type GtkImage to a GtkButton, but as a GtkBin subclass a GtkButton can only contain one widget at a time; it already contains a widget of type GtkLabel

(cheese:3700): Gtk-WARNING **: Attempting to add a widget with type GtkHBox to a GtkToggleButton, but as a GtkBin subclass a GtkToggleButton can only contain one widget at a time; it already contains a widget of type GtkLabel

(cheese:3700): Gtk-WARNING **: Attempting to add a widget with type GtkImage to a GtkButton, but as a GtkBin subclass a GtkButton can only contain one widget at a time; it already contains a widget of type GtkLabel
libv4l2: error turning on stream: &#1054;&#1096;&#1080;&#1073;&#1082;&#1072; &#1087;&#1088;&#1086;&#1090;&#1086;&#1082;&#1086;&#1083;&#1072;

** (cheese:3700): WARNING **: Error starting streaming on device '/dev/video0'.


** (cheese:3700): WARNING **: Could not negotiate format
I have an Ubuntu 11.10. It is Asus N61Jv .

i have tried > ls -l /dev/video*sometimes it shows
> crw-rw----+ 1 root video 81, 0 2012-02-02 20:02 /dev/video0
and sometimes > crw-rw----+ 1 root video 81, 1 2012-02-02 20:04 /dev/video1
it switches after every launch of Cheese. oh and also the message of Cheese itself switches every time between
> ** (cheese:3700): WARNING **: Error starting streaming on device '/dev/video0'.and
> ** (cheese:3700): WARNING **: Error starting streaming on device '/dev/video1'.
thanks in advance

---

### Post by jlucasps on 2012-02-04
Same problem :-/

Can anyone help us.

Thanks in advance.

---

### Post by unrater on 2012-06-21
I have the same problem. For the programmers, i think this webcam has a bit that is used has lock to prevent concurrency on the same hardware.

And, because of that, when some program is interrupted, the bit is not altered and considered always blocked. I think this is what's happening because if i take of the battery some time, then the webcam is available!

---

### Post by unrater on 2012-07-15
no asnwers? :'(

---

