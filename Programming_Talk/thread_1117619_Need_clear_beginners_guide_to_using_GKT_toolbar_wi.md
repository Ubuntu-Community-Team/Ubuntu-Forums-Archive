---
title: "Need clear beginners guide to using GKT toolbar with icons"
date: 2009-04-06
forum: Programming Talk
---

### Post by anewguy on 2009-04-06
Been trying to get going on my second GTK application.  This one requires toolbar with icons.  What I want is a toolbar with icons, and when I click on an icon to have it changed to look like it is pressed and stay that way until I do something else.

I've been trying like heck to follow the following tutorial, but I just end up with a mess - pointers to pointers that aren't defined, syntax errors that make no sense to me, etc..  I've been trying to follow the part where it builds an icon from a XPM file, but when I put their sample XPM in a file and include that file, it then bombs out saying gtk.XPM isn't defined.  I am starting to get confused and wish I could find a guide that states in simple terms "define the toolbar as x", "define these widgets, etc., as they are needed", "define your icons as A, build the widgets from them with B", etc..  

I hate to sound so dang stupid but I'm just starting out on this.  My "C" programming is so rusty I really don't know what the definitions mean that I find that say things like:

gtk_xxx_yyy(GtkContainer (*container),
            ..
            ..
            ..

I see these a lot in the gtk reference guide (and in just general "C" documentation).  I just don't know how to read them anymore.


[http://www.gtk.org/tutorial1.2/gtk_tut-10.html#ss10.11]("http://www.gtk.org/tutorial1.2/gtk_tut-10.html#ss10.11")


Any help and pointers to more simple beginners guides for using toolbar, icons, etc., would be greatly appreciated!

Thanks in advance!
Dave :)

---

### Post by cabalas on 2009-04-06
Have you tried using glade (which is available in the repos) to design your user interfaces, it will take a lot of the hassles that you are experiencing out of the picture.

As a side note that tutorial you are using is woefully out of date you might want to take a look at this one instead - [http://library.gnome.org/devel/gtk-tutorial/stable/](http://library.gnome.org/devel/gtk-tutorial/stable/)

---

### Post by anewguy on 2009-04-06
I've looked at glade a few times, guess I need to try it more and learn to interface with it from C.  Thanks for the heads up on the tutorial - it seemed very different from others I had seen but didn't understand.  I'll take a look a the one you mentioned.

Thanks!
dave :)

---

### Post by anewguy on 2009-04-06
Here's some of the things I run into when trying to use Glade:

- I can't seem to be able to set the size of widgets correctly on the screen in Glade.  I have main vboxes - 1 for the menu line, 1 for the toolbar, and one for the rest of the display (which varies).  If I want a horizontal line with 5 parts to it - space, label, space, text area, space, I cannot figure how in Glade to set the size of the objects.  Heterogenious or not doesn't make any difference as it doesn't let me adjust the size of each object.

Dave ;)

---

