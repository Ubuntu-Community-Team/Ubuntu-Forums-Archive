---
title: "GTK and C, multiple menu lines"
date: 2009-04-01
forum: Programming Talk
---

### Post by anewguy on 2009-04-01
I adapted/wrote one other application to use GTK, but never did figure something out that I need help on for the project I am working on now:

I define a main menu bar, and append in the drop-down items and pack the menu items into the menu bar, pack it to a vbox, and do the appropriate shows and everything looks good.

I copied the same routines (just to test) and changed widget names and create a second menu bar.  I then pack the menu bar into another vbox, do the shows, and all I see is the first menu bar - the second never shows.

All I have defined as far as containers go is:

window -> the only defined container
-vbox1
------menubar 1 with drop-downs
-vbox2
------menubar 2 with drop-downs

After appending the drop-downs into the menu items, I then append the menu items onto the menu bar.  Then I pack the menubar into the vbox and show the vbox.

I then do the same thing but with different widget names and using vbox.  Vbox2 just doesn't seem to appear anywhere on the screen.

Sometimes I wonder if I'm getting mixed up using a vbox when maybe I should be using a hbox, but I thought vbox's showed their contents left to right, where hbox's showed theirs top to bottom.

I also would like to know how to size widgets based on windows width, window height, and font size being used in the widget.  I have found mention of some gets for window geometry, but I don't know how to use what I get to set the values on widgets.  If the window height is "x", and I have 4 boxes to go in it, I don't want those to be equal sized.  Some I may want to set based on font size, etc..

Any help for this struggling beginner would be greatly appreciated!!

Thanks in advance!
Dave :)

---

### Post by moma on 2009-04-01
I do often use glade-2 interface designer to mockup an UI for my GTK-programs.

Install and run glade-2
$ sudo aptitude install glade-2
$ glade-2

Now design your user interface or part of the UI that you find difficult to create in c.

Start with a "Window" widget then add Vertical box (VBox) with at least 4 rows. 
* Put a menubar at the top. 

* Add your handle+toolbar widget in the second row. Handle makes the toolbar detachable/moveable. 
  Later modify and add buttons (or eg. your combobox) to it.

* Add components for your UI in the third row.

* Add a statusbar (status line) at the bottom. 

Take a look at this picture:
[http://bildr.no/view/380188](http://bildr.no/view/380188)
[[img]http://bildr.no/thumb/380188.jpeg[/img]](http://bildr.no/view/380188)

Here is the code: [http://www.edbl.no/tmp/project9.tar.gz](http://www.edbl.no/tmp/project9.tar.gz)
Unpack the files and open project9.glade in glade-2. Or just clik on the project9.glade file in file manager. Actually, this kind of glade-project will give a good starting point because it includes a Makefile and support for language translation etc.
--------------

I often need to use several VBox and Hboxes inside each other to get satisfactory result.
Check the glade-2s "View"menu and show all the appropriate help windows such as "show widget tree" and "show properties window".

When you're ready with your mockup, "Save" it and "Build" it. (these are toolbar-buttons in the glade-2's window). 
It will generate and put a ready-made c code (normally in) $HOME/Projects/project#/src/interface.c file. Open it and clip & paste code to your GTK-project.

You can also compile and test the generated glade-2 code directly. Just run 
$ ./autogen.sh
$ make 
in the project# directory.  Then run the binary
$ src/project#
--------------

Of course you can build your entire GTK-project around a .glade file without any particular c-code for the UI. But as said, I just open the src/interface.c in gedit and copy & paste those pieces of code I need.

BTW: Why would you have 2 menubars at the top? Maybe you should have 1 menubar and several toolbars. Add your drop-down listbox to a toolbar.  
Take a look at the Gscreendump app below. It has one menubar and one detachable toolbar. (easy to add any number of toolbars).
--------------

ps. Do not forget to check my [Gscreendump project...]("http://code.google.com/p/gscreendump/wiki/PicturesAndScreenshots") It's a revolutionary screenshot tool with many amazing features. You can also study the C code. It's pure GTK/GDK + some Xlib.

[COLOR="Red"]EDIT:[/COLOR] A mistake in the explanation. Handle belongs to a toolbar, not menubar.

[COLOR="Red"]EDIT:[/COLOR] Very important reference guide to GTK/GDK developers: [http://library.gnome.org/devel/gtk/stable/](http://library.gnome.org/devel/gtk/stable/)
You can search both GTK and GDK functions.

---

### Post by anewguy on 2009-04-01
Thanks for the reply.  I am trying to make a GUI similar to that of the Family Tree Maker genealogy program I run in Windows.  It has a main menu bar followed below by another menu bar.  If I can ever get enough of GTK figured out for this then I'll move on to a MySql database design for storing the data so that I can gradually add 1 functionality at a time.  

My other GTK project I developed on Ubuntu then ported to Windows with GTK with hardly any modifications.  The modifications that were made where compiler directives so I could do such things as concantenate paths, etc., correctly for each OS.  This time I am trying to develop in Windows with GTK and then move to Linux.  With what I learned on the first project that should be easy.  But with that said, I don't think they make a version of Glade for Windows.  I could always boot into Linux and try it so I can see the code, then pull it over to Windows.

My C knowledge is EXTREMELY rusty, so when I see the defs in some of the GTK guides on line, I get lost as to how to try to use them.  So, as dumb as it sounds, doing all the screen work in GTK for all of the various ways the data can be shown is going to be the real challenge for me.

EDIT:  Found solution - I wasn't appending into the correct menu item, so 2nd menu didn't really exist.

Thanks again!
Dave :)

---

