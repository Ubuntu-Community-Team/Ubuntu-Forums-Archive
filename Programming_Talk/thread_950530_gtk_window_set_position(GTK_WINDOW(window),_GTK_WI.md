---
title: "gtk_window_set_position(GTK_WINDOW(window), GTK_WIN_POS_CENTER)"
date: 2008-10-17
forum: Programming Talk
---

### Post by Jonas thomas on 2008-10-17
Hi,
I'm sort of a newbie at Gtk+ so please cut me some slack if this is a real stupid question.
I've been working through a [tutorial]("http://zetcode.com/tutorials/gtktutorial/firstprograms/") on Gtk+  line by line and going back and forth through [GTK+ Reference Manual]("http://library.gnome.org/devel/gtk/2.14/gtk-General.html") to see if everything makes sense.

Things started getting a little fuzzy when I got got to:
```
gtk_window_set_position(GTK_WINDOW(window), GTK_WIN_POS_CENTER);
```
Ok... so.....
gtk_window_set_position is a function.
GTK_WIN_POS_CENTER is a enum
window is a Pointer to a data structure GtkWidget
This makes sense to me...
What's the deal with the GTK_WINDOW()?
I guess this is a give the man a fish or teach him how to fish question.
I went through the reference documentation they say that GTK_WINDOW() is a [preprocessor?] MACRO and that macro's are not really discussed that well in the documentation.:(

What's the easiest way to trace down which header file GTK_WINDOW() is defined so I can study it and figure out what this does? Manually searching through the header files holds no appeal to me.
Thanks,
JT

---

### Post by cl333r on 2008-10-17
GTK_WINDOW() is a macro to cast the widget. For more info google "GTK_WINDOW macro".

---

### Post by nvteighen on 2008-10-17
The macro is there because you're in C, which is not a true OOP language, even if you spice it up to a OOP-like state by using libraries like GLib (which is part of GTK+, but you can use it on your programs separately). 

In OOP languages like C++, Java, Python, Ruby, Perl, Common Lisp, etc., you can have an object that not only is of some class, but also belongs to a hierarchically superior class. For example: you can have a class for dogs, but dogs are also mammals, so any dog "object" will automatically **inherit** the proprierties related to mammals. These languages are meant to allow you look at the same object from different but ordered points of view in a very easy way.

But C is not OOP. The nearest you can do is to create data structures, play around with static functions and create something similar to OOP, but without proper automatic inheritance. Therefore, you have a GtkWindow, but declared as a GtkWidget (the most superior level in the class hierarchy), and gtk_window_set_position(), obviously, asks for a GtkWindow... So, you have to cast them in order to tell the program that that GtkWidget is meant to be used this time as a GtkWindow... but you could cast it to a GObject (e.g. when using the g_signal_connect() function to connect an action to some event on the GObject... which is a GLib "class").

If you use GTK+ in C++ or in Python, you avoid all these hassles.

---

### Post by Jonas thomas on 2008-10-17
> **nvteighen said:**
> The macro is there because you're in C, which is not a true OOP language, even if you spice it up to a OOP-like state by using libraries like GLib (which is part of GTK+, but you can use it on your programs separately). 

In OOP languages like C++, Java, Python, Ruby, Perl, Common Lisp, etc., you can have an object that not only is of some class, but also belongs to a hierarchically superior class. For example: you can have a class for dogs, but dogs are also mammals, so any dog "object" will automatically **inherit** the proprierties related to mammals. These languages are meant to allow you look at the same object from different but ordered points of view in a very easy way.

But C is not OOP. The nearest you can do is to create data structures, play around with static functions and create something similar to OOP, but without proper automatic inheritance. Therefore, you have a GtkWindow, but declared as a GtkWidget (the most superior level in the class hierarchy), and gtk_window_set_position(), obviously, asks for a GtkWindow... So, you have to cast them in order to tell the program that that GtkWidget is meant to be used this time as a GtkWindow... but you could cast it to a GObject (e.g. when using the g_signal_connect() function to connect an action to some event on the GObject... which is a GLib "class").

If you use GTK+ in C++ or in Python, you avoid all these hassles.

I sort have googled an haven't really found the answer to satisfy my curiosity yet...
If I understand what I've read is that this macro casting stuff is they're trying to use objects in C instead C++ 
I so some reference to it in.[http://docs.mandragor.org/files/Operating_systems/Linux/GTK_Gnome_Application_Development_en/cha-objects.html]("http://docs.mandragor.org/files/Operating_systems/Linux/GTK_Gnome_Application_Development_en/cha-objects.html")

Isn't Macro in C is a pre-processor directive?? So the implementation should be viewable in a header file somewhere right?? So I guess my question is If want to take a look at it, what's the easiest way to find it??

---

### Post by nvteighen on 2008-10-18
> **Jonas thomas said:**
> I sort have googled an haven't really found the answer to satisfy my curiosity yet...
If I understand what I've read is that this macro casting stuff is they're trying to use objects in C instead C++ 
I so some reference to it in.[http://docs.mandragor.org/files/Operating_systems/Linux/GTK_Gnome_Application_Development_en/cha-objects.html]("http://docs.mandragor.org/files/Operating_systems/Linux/GTK_Gnome_Application_Development_en/cha-objects.html")

Isn't Macro in C is a pre-processor directive?? So the implementation should be viewable in a header file somewhere right?? So I guess my question is If want to take a look at it, what's the easiest way to find it??
From /usr/include/gtk-2.0/gtk/gtkwindow.h:
```

#define GTK_WINDOW(obj)			(G_TYPE_CHECK_INSTANCE_CAST ((obj), GTK_TYPE_WINDOW, GtkWindow))

```

Of course, you now need to look at what G_TYPE_CHECK_INSTANCE_CAST() is... which I fear it has to be lost somewhere in GLib's source... :p

---

### Post by Jonas thomas on 2008-10-18
> **nvteighen said:**
> From /usr/include/gtk-2.0/gtk/gtkwindow.h:
```

#define GTK_WINDOW(obj)			(G_TYPE_CHECK_INSTANCE_CAST ((obj), GTK_TYPE_WINDOW, GtkWindow))

```

Of course, you now need to look at what G_TYPE_CHECK_INSTANCE_CAST() is... which I fear it has to be lost somewhere in GLib's source... :p

Thank you for your concise answers.  They make sense to me. I'm actually more interested in pursuing GTK+ in C++ then I am in C.  So I guess for my purposes I should stop digging trying to understand what's going here with this casting stuff. Unfortunately, I haven't [yet] run across a online tutorial for GTK++/C++ as nice as the one I've seen for [C]("http://zetcode.com/tutorials/gtktutorial/firstprograms/").  
Any chance you have some favorite bookmarks you can recommend for GTK+/C++ newbies?

My primary goal in all this is to understand GTK+ sufficiently so I can start playing around with opencascade library.  I found a [source ]("http://myweb.tiscali.co.uk/dolbey/GtkOpenCascade/index.htm")applications which use GTK+ viewer and the opencascade library. 
Thanks,
JT
[EDIT] I believe what I'm looking for is [gtkmm]("http://www.gtkmm.org/")

---

### Post by nvteighen on 2008-10-19
Yes, what you need is gtkmm... 

Sorry, I don't know C++, but I fear that it shouldn't be too different to "real" GTK+ (gtkmm is just a wrapper, not a whole GTK+ written from scratch in C++), so the knowledge you have is entirely valid. Just that instead of using casts or the gtk_object_do_this(object, arg) syntax, I'm sure you have to use object.do_this(args)... at least that's how GTK+ is translated to Python (another OOP language).

---

### Post by Jonas thomas on 2008-10-19
> **nvteighen said:**
> Yes, what you need is gtkmm... 

Sorry, I don't know C++, but I fear that it shouldn't be too different to "real" GTK+ (gtkmm is just a wrapper, not a whole GTK+ written from scratch in C++), so the knowledge you have is entirely valid. Just that instead of using casts or the gtk_object_do_this(object, arg) syntax, I'm sure you have to use object.do_this(args)... at least that's how GTK+ is translated to Python (another OOP language).

In case your interested in learning C++, I stumbled on this gem of a [free on-line course]("http://esmane.physics.lsa.umich.edu/wlap-cwis/SPT--BrowseResources.php?ParentId=215") in C++ by Paul Kunz. I have a [post]("http://ubuntuforums.org/showthread.php?t=918896") on the forum about it. I feel it was very worth while. The only issue is I could never get it running well in Linux and had to use my wife's W2k machine.
JT

---

### Post by nvteighen on 2008-10-19
> **Jonas thomas said:**
> In case your interested in learning C++, I stumbled on this gem of a [free on-line course]("http://esmane.physics.lsa.umich.edu/wlap-cwis/SPT--BrowseResources.php?ParentId=215") in C++ by Paul Kunz. I have a [post]("http://ubuntuforums.org/showthread.php?t=918896") on the forum about it. I feel it was very worth while. The only issue is I could never get it running well in Linux and had to use my wife's W2k machine.
JT
Actually, and no offense meant, I don't consider to learn C++, at least in the near future. I'm a hobbyist and mostly interested on higher abstraction level languages (specially Lisp). But anyway, thanks!

---

### Post by Jonas thomas on 2008-10-19
> **nvteighen said:**
> Actually, and no offense meant, I don't consider to learn C++, at least in the near future. I'm a hobbyist and mostly interested on higher abstraction level languages (specially Lisp). But anyway, thanks!

No offense taken. I too am a hobbyist but for the moment C++ is of  great interest to me.  Perhaps are paths will cross again...

---

