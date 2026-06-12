---
title: "C and GTK about transferring buttons"
date: 2009-09-07
forum: Programming Talk
---

### Post by slurrrp on 2009-09-07
I have two windows. One of them has an array of buttons, and the other window is empty. I have to be able to "transfer" the buttons from one window to another and back when pressed. I heard about destroying then creating the button, but I can't seem to find a way to do it.

I don't know how to do this since I am quite new with gtk. Can anyone help me out here?

---

### Post by moma on 2009-09-07
Hello,

It's quite easy to destroy and create widgets on the fly.
Take this Gscreendump project
[http://code.google.com/p/gscreendump/](http://code.google.com/p/gscreendump/)

And open src/sd_imagick_dialog.c file and look for functions:
 void imagick_clear_dialog();
 void imagick_create_command_dialog(int index);

First, create a GTK_CONTAINER (vbox or hbox) wherein you can put your widgets. See the imagick_clear_dialog() function for how to destroy/remove widgets from the container.

---

