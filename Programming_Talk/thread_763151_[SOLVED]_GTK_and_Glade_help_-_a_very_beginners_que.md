---
title: "[SOLVED] GTK and Glade help - a very beginners question"
date: 2008-04-22
forum: Programming Talk
---

### Post by anewguy on 2008-04-22
I have an application in C that currently only runs from the command line and issues messages back to the terminal as to the status of it's operations.  I want to make a GUI'd front end to this that is really simple - a button to press to start the normal C code, and a text area that I can change the C code to output to.  So far, I am at the VERY beginnings of this, and GTK and GLADE are all new things to me.

At this point, I have been following one of the online tutorials and have done just the 1st step from there - created a window with nothing in it and allow it to be closed.  Here's is my first of what will probably be many dumb questions:

the code had a similar line to this, I just modified it to put my own function in the call back:

    glade_xml_signal_connect (gxml, "on_window1_destroy",
                              G_CALLBACK (my_main_quit));

It runs ok, but I can't ever get it to actually stop (when started from the command line via ./progname) even after the window has closed.  Do I need to put in some sort of exit statement in the my_main_quit function to actually get the program to end?  The way I understand it, the opening "program" describes the window and the operations (functions) that are to take place when a signal comes back from a widget (like the button click).  I noticed that main function does a return 0 after it shows the window and does a gtk_main().  Inside my "quit" function, what would I need to put in to actually stop the program, and do I need to include anything to clean up any remaining GTK things or are they owned by my process and thereby die when it dies?

Sorry for such basic questions, but I am really rusty at C, never learned C++, and have never used GTK and Glade before!  :)

---

### Post by sq377 on 2008-04-22
instead of ```
glade_xml_signal_connect (gxml, "on_window1_destroy",
G_CALLBACK (my_main_quit));
```
try this
```
GtkWidget *window = glade_xml_get_widget(gxml, "window1");
g_signal_connect(window, "destroy", G_CALLBACK(my_main_quit), NULL);
```

This is the only way I've ever done it

---

### Post by anewguy on 2008-04-22
Thanks for the reply!  I tried that but get the same result - maybe I'm thinking wrong on this, but if I do ./progname and then close the window it creates, I should be returned to the command line.  Instead it just hangs there until I do a ctrl-c.

Here's the link I've been following, and you'll see I'm at the very beginning of all this.  The program itself runs - the window comes, I close the window.  It just never returns to the command line.

[http://www.micahcarrick.com/12-24-2007/gtk-glade-tutorial-part-1.html]("http://www.micahcarrick.com/12-24-2007/gtk-glade-tutorial-part-1.html")

:)

---

### Post by sq377 on 2008-04-22
Maybe there is something wrong with your destroy function.  Try this instead:
```
g_signal_connect(window, "destroy", G_CALLBACK(gtk_main_quit), NULL);
```
If that doesn't work, could you paste the complete code?

---

### Post by anewguy on 2008-04-23
Bearing with me being a beginner, I hope you'll forgive that I blew everything away to start over again, and just haven't got that info for you right now.  However, I think I may know what's wrong - please correct me if I'm wrong:

clicking "quit" on a file menu would result in the destroy - I think it would be another thing if you just clicked the "X" to close the window, and I think that is the catch in this case.  Right now I don't know the terminology to now if that what be considered another method or what, but I suspect it returns something other than the destroy window, and the form did not have a menu on it yet so there was no file/quit option so no destroy window signal was generated?  Does that make sense?

Thanks! :)

---

### Post by haTem on 2008-04-23
Closing the window by clicking the "X" does generate the "destroy" signal. You have to tell GTK what you want it to do when that happens. You were on the right track, no need to start over :).

[PHP]gtk_main();[/PHP] This starts a "main loop" that checks for events until you tell it to stop.

To actually make it stop, you have to call:

[PHP] gtk_main_quit();[/PHP]

Normally, you can just do the following (as sq377 said):
[PHP]GtkWidget *window = glade_xml_get_widget(gxml, "window1");
g_signal_connect(window, "destroy", G_CALLBACK(gtk_main_quit), NULL);[/PHP]

That will call gtk_main_quit() directly when the window emits the "destroy" signal.

Or you could have it call a custom quit function, if you want to do some cleaning up before exiting:
[PHP]GtkWidget *window = glade_xml_get_widget(gxml, "window1");
g_signal_connect(window, "destroy", G_CALLBACK(my_main_quit), NULL);[/PHP]

Just make sure that inside "my_main_quit" you are calling gtk_main_quit(), otherwise the "main loop" will continue to run and it will hang until you kill it as you experienced.

Hope that helps, I usually use gtkmm so I may be off here :-P. Let me know how it goes.

- Hatem

---

### Post by anewguy on 2008-04-23
Thanks for the reply!  So I was going okay based on the tutorial - I just can't figure out why, after it closed the window, I was not returned to the command line  (I ran it from a terminal window with ./progname)  until I pressed ctrl-c - it acted like it shutdown the gtk stuff as far as the window is concerned, but never acted like the whole process quit.  I'll try it again later and post back what happens.

BTW - I just want a simple screen -> menu bar I have figured out, I found out from the tutorial how to divide the screen up and then add widgets, and I only need 2 buttons (1 basically for "go", the other for "exit") and a output-only scrolling text window I can write to.  Since I am using Glade 2 Interface Designer (I tried version 3.?? but it didn't seem to work right), I have it outputting just C code instead of C++, so I can see how it will be simple on a click of button 1 to just put a function call to what used to be the main part of the terminal based program.  I'm a little stuck at what type of widget I use for a output-only scrolling text box and how to write 1 line at a time to that widget and let it automatically scroll.

Could either of you perhaps just put in pretty simple terms (widget x, write to it via gtk_xxxxxxxx) how to do that.  I don't need sample code, as I think I'll learn more trying to figure that out on my own.  I just need a little pointing in the right direction!  :)

Thanks, everyone!  :)


EDIT: Another cry for help:  Instead of handcoding this time I let Glade create the code.  There is a main directory with a couple of directories under it.  I have NO CLUE what the heck to do to compile this now.  I tried ./configure, but configure wasn't found.  I tried autgen configure.in, but still never got a configure file.  Tried just make, and obviously that didn't work. So far the pieces to the tutorials I have been using on line don't say squat on how to actually use the output from Glade.

---

### Post by anewguy on 2008-04-23
Hey guys!!  It worked!!  I finally figured out to run autoconf without specifying the configure.in file name and then just run make - worked like a champ!  In addition, I changed the signal handling as you recommended to g_signal_connect......  AND, I think changing "on window1 destroy" to just "destroy" did the trick!.  Now I can add in the simple things - the menu quit signal handler, the menu help about signal handler and my own "exit" button signal handler.  Still don't know about using the scrolling text window.  When I can get that figured out I think the rest (at least it SEEMS that way [yikes!!]) will go pretty good.

Any input on the "output-only scrolling text box write 1 line at a time" thingy??  :):)

thanks for your help so far - it's been great!  :)

---

### Post by haTem on 2008-04-23
Nice job!

AFAIK, generating code with glade is not recommended and it was dropped from glade-3, so be careful with that :-P.

For the text output, you can try a textbuffer/textview combination.

Create a GtkTextBuffer widget, it holds the actual text, but it doesn't display it.

Then create a GtkTextView, it's the widget that actually displays the text. To tell it to use the text buffer you created (so it knows what to display) you can use gtk_text_view_set_buffer.

To add text, you can use gtk_text_buffer_set_text.

To make it output-only, you can use gtk_text_view_set_editable.

Check out the api and lookup the functions I mentioned so you know how they're used:

[http://library.gnome.org/devel/gtk/unstable/GtkTextBuffer.html](http://library.gnome.org/devel/gtk/unstable/GtkTextBuffer.html)
[http://library.gnome.org/devel/gtk/unstable/GtkTextView.html](http://library.gnome.org/devel/gtk/unstable/GtkTextView.html)

Good luck and have fun!

- Hatem

---

### Post by RIchard James13 on 2008-04-23
To get a scrolling text display you need to use a TextView widget (GtkTextView). That should scroll but will not have any scroll bars. So first place a ScrolledWindow (GtkScrolledWindow) somewhere on your form/window and then place the TextView Widget inside the ScrolledWindow Widget. This should give you what you scrolling text with scroll bars. However you don't write to the TextView, you create in your program a GtkTextBuffer and bind that to the TextView. You can see demo code of that in the GTK Documentation 
[http://library.gnome.org/devel/gtk/stable/TextWidget.html]("http://library.gnome.org/devel/gtk/stable/TextWidget.html")

Docs on the GtkScrolledWindow
[http://library.gnome.org/devel/gtk/stable/GtkScrolledWindow.html]("http://library.gnome.org/devel/gtk/stable/GtkScrolledWindow.html")

---

### Post by anewguy on 2008-04-23
Thanks, guys!  I tried the code generated by version 2 and it worked, so then I tried modifying it to fit more along the lines of the tutorial, along with the suggestions, and now I can't get it to compile again.  Guess I'll just keep hammering at it until something gives!!  Thanks for the heads up on the "scrolling text box thingy" and the links for more info on using the interface.  I had only found 2 tutorials so far so the extra ones really help!

Thanks again!! :):)

---

### Post by anewguy on 2008-04-23
Okay, I admit I'm stuck.  Can you point me to any VERY beginners guides?  The tutorial I was following doesn't show how to declare and then pass the Gtk pointers to other functions (like if I have my own "shutdown" function).  I've looked at some of the documentation about GTK and it is obviously a reference for those who already know what they are doing (reminds me a lot of the old system manuals for the big hardware I worked with years past).  Obviously, "I got no clue".  :)

---

### Post by Can+~ on 2008-04-24
> **anewguy said:**
> Okay, I admit I'm stuck.  Can you point me to any VERY beginners guides?  The tutorial I was following doesn't show how to declare and then pass the Gtk pointers to other functions (like if I have my own "shutdown" function).  I've looked at some of the documentation about GTK and it is obviously a reference for those who already know what they are doing (reminds me a lot of the old system manuals for the big hardware I worked with years past).  Obviously, "I got no clue".  :)

I don't want to push anyone, but if you want to go even easier, go with python. I tried GTK with C, and my head just blew up trying to sort my pointers properly, and keeping track of what I did.

Typical example with glade:

[PHP]#!/usr/bin/env python
#Python with GTK source file.

import gtk, gtk.glade

class mainWindow:
	def event_destroy(self, widget, data=None):
		gtk.main_quit()
	
	def event_debug(self, widget, data=None):
		print "widget %s called with data %s" % (widget, data)
	
	def __init__(self):
		self.xml = gtk.glade.XML("gladefile.glade")
		self.win = self.xml.get_widget("window1")

		#Signals
		signals = { 
		"event_destroy"	: self.event_destroy,
		"event_debug" 	: self.event_debug }
		
		self.win.connect("destroy", event_destroy)
		self.xml.signal_autoconnect(signals)
		
		self.win.show_all()

	def main(self):
		gtk.main()

if __name__ == "__main__":
	mwin = mainWindow()
	mwin.main()[/PHP]

---

### Post by RIchard James13 on 2008-04-24
Which tutorial are you using?
I am using the one from here 
[http://library.gnome.org/devel/gtk-tutorial/stable]("http://library.gnome.org/devel/gtk-tutorial/stable")

---

### Post by anewguy on 2008-04-24
Can+~  => right now I have an application all in C that I run through a terminal window on the command line.  I just want to make a GUI'd front-end to it.

RIchard James13  =>  That tutorial looks promising.  I had been using a small one that shows how to create the hello world program using GLADE designer and a very simple piece of code.  I'm on now to where I need to really figure out what to do for the app and how to get all the different .c files to be used from a main program using Gtk.  Basically I want (amongst other little things) a button then when clicked will call the main .c file for the terminal application, and then just change various .c files from it to display back to that window.  I'm extremely rusty at C right now, and it took me about 2 months to combine 2 programs into 1 overall program that runs in terminal.  So, things like pointers to pointers, etc., are almost as good as new to me right now.  I hope some will click in place.  I think the tutorial you linked will help me quite a bit!  Thanks!  :)

---

