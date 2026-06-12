---
title: "[gtkmm Glade C++] Connecting signals in Glade"
date: 2008-11-14
forum: Programming Talk
---

### Post by AntoineL on 2008-11-14
I am new to Linux/GNOME programming. I know C and I just learned the basics of C++.

I am considering using C++ to develop applications with Glade and gtkmm.

I have googled a bit and read parts of the book on [www.gtkmm.org](www.gtkmm.org). From what I understand, when you code your app in C, you can design the UI in Glade, and do all the signals connecting from there. Is there a way to do the same thing in C++? Doing all the connecting in the code seems a bit awkward to me.

Should I stick to C instead of going "big" with C++ ?

---

### Post by samjh on 2008-11-14
It's really not that hard.

In libglade (the C version), there is an autoconnect feature.  You set the handler names in the Glade file, and in your C code, you made handler functions the same as the handler names in the Glade file.

In libglademm (the C++ version), there is no autoconnect feature.  The signal connecting code is only one line, and not hard to write at all.

Here's a comparison.  There are two signals in the Glade file: on_hellowindow_destroy and on_greetbutton_clicked.  In the C version, the autoconnect feature will automatically connect the signals to the widget.  In the C++ version, it is done by hand.

**C**
```
// global stuff...
GladeXML* xml;

void on_hellowindow_destroy(GtkWidget* widget)
{
	// a signal handler...
}

void on_greetbutton_clicked(GtkWidget* widget)
{
	// another signal handler...
}

int main(int argc, char* argv[])
{
	// ...
	
	xml = glade_xml_new("hello.glade", NULL, NULL);

	// ...

	glade_xml_signal_autoconnect(xml);

	// ...
}
```

**C++**
```
// global stuff...
Gtk::Button* greetbutton;

void on_greetbutton_clicked()
{
	// a signal handler...
}

int main(int argc, char* argv[])
{
	// ...

	Glib::RefPtr<Gnome::Glade::Xml> refXml;
	refXml = Gnome::Glade::Xml::create("hello.glade");
	
	// ...
	
	greetbutton->signal_clicked().connect(sigc::ptr_fun(on_greetbutton_clicked));
	
	// ...
}
```

---

### Post by AntoineL on 2008-11-14
Thanks for the quick reply.

In the C version, you execute one function to connect all the signals of the XML file. In the C++, you have to connect every signal individually, without ever looking at the XML file.

From what I see, C offers better separation from UI than C++. But C++ has the object abstraction.

I think I'll stick to C++ as planned, and have a look at C if C++ gets too nasty.

---

### Post by vdawg on 2010-08-15
I'm just starting out with GTK and C++ myself :)

From my research, it seems that GTK and python go very well together and there's some pretty good documentation out there as well.

As for me, I'm just basically looking to keep my C++ up to speed :P

---

### Post by worksofcraft on 2010-08-16
Per chance I was researching this recently my thread:
[http://ubuntuforums.org/showthread.php?t=1551841](http://ubuntuforums.org/showthread.php?t=1551841)
There I started by C++izing a C program and soon realized it is better do a full object oriented design.

I posted on an appropriate mailing list and had a very helpful reply confirming that as yet there is no support in gtkmm to connect all the signals in one go.

What I found is that in C++ you can connect member functions, whereas in C you have to get your static/global signal handlers to operate on other objects. That means type casting pointers, or using global data and it all ends up very messy and unsafe.

So the expedience of having all the signals connected as specified in the .glade file is completely negated by the extra complexity.

---

### Post by lupusnoctu on 2010-11-17
> **worksofcraft said:**
> Per chance I was researching this recently my thread:
[http://ubuntuforums.org/showthread.php?t=1551841](http://ubuntuforums.org/showthread.php?t=1551841)
There I started by C++izing a C program and soon realized it is better do a full object oriented design.

I posted on an appropriate mailing list and had a very helpful reply confirming that as yet there is no support in gtkmm to connect all the signals in one go.

What I found is that in C++ you can connect member functions, whereas in C you have to get your static/global signal handlers to operate on other objects. That means type casting pointers, or using global data and it all ends up very messy and unsafe.

So the expedience of having all the signals connected as specified in the .glade file is completely negated by the extra complexity.

so, what you're saying then is that C++ and GTKmm is the better choice as it results cleaner code and a more stable, robust program?

Any idea if GTKmm plans to add an auto-connect feature any time soon?

Is it better to use GtkBuilder or libglade format in glade? 

What about using libglademm? Is the process any different between the other two and libglademm?

These are some of the questions that have been bothering me for some time, and preventing me from fully switching over to programming with UIs. Before now, every thing I've done has been either on a console or it has been headless.

---

### Post by worksofcraft on 2010-11-17
> **lupusnoctu said:**
> so, what you're saying then is that C++ and GTKmm is the better choice as it results cleaner code and a more stable, robust program?


Yes, but I've found a way to use the autoconnect feature in C++ now:

The reason it won't work is that C++ has "name mangling" to guarantee function parameter type safety at link time.

To enable the auto-connect to recognize your call back function names all you have to do is suppress their name mangling:

[php]
// GUI call back functions: must suppress C++ name mangling
extern "C" {
	gboolean on_click(
		GtkWidget *widget,
		GdkEventButton *event,
		graphplacement *user_data
	) {
		gtk_widget_queue_draw(widget);
		return true;
	}
... etc
} // end name mangling suppression
[/php]

Notice how I can simply declare my *user_data to be what ever class I want and it's my own fault if I got it wrong and it crashes!

> 
Is it better to use GtkBuilder or libglade format in glade?


I think libglade is being deprecated: a feature from when glade used to generate code for you. In any case I stick to GtkBuilder as it does everything I want it to :)

p.s. remember to include gmodule if you want to use the auto connect. Here is a typical compile command I might use:
```

g++ thedata.cpp *.o `pkg-config --cflags --libs cairo gtkmm-2.4 gtk+-2.0 gmodule-2.0`

```
Note: That is taken from my proof-of concept code for [Schematrix]("http://code.google.com/p/schematrix/downloads/list") but I'm now exploring the use of [AGG, Anti Grain Graphics]("http://antigrain.com/") and using garbage collection with C++ before progressing with that.

---

### Post by lupusnoctu on 2010-11-17
Thank you for the reply. That has helped answer a couple of things, but what exactly is that structure, and how does it work? You've failed to explain any of it, even in your source code for Schematrix. A college student might understand that structure without issue, but someone who is learning on his own while trying to get his GED so he CAN go to college (referring to myself here) would have a much harder time with that.

---

### Post by worksofcraft on 2010-11-17
> **lupusnoctu said:**
> Thank you for the reply. That has helped answer a couple of things, but what exactly is that structure, and how does it work? You've failed to explain any of it, even in your source code for Schematrix. A college student might understand that structure without issue, but someone who is learning on his own while trying to get his GED so he CAN go to college (referring to myself here) would have a much harder time with that.

I shall be pleased to explain. I just never know who might be reading and like you I am teaching myself how to program because I'm actually a hardware engineer by trade.

Anyway... so the call back functions are called from GUI widgets but the operation they need to do, in general, doesn't apply to that particular widget. Thus Gtk allows you to pass a pointer to "user data" for use by your call backs functions. In my main is the code:
[php]
	// Connect Gtk call-backs
	gtk_builder_connect_signals(pBob, qRoot);
[/php]

Here pBob is a pointer to a GtkBuilder (soz, I called him Bob after "Bob the builder")
[IMG]http://www.sirearevalo.com/wp-content/uploads/2009/05/bob-the-builder-icon-v8.jpg[/IMG]

qRoot is a pointer to my "user data". The q I use to remind me that it points to something that was dynamically allocated and so I'll have to dispose of it at some stage.

The user data in that particular application is not in anyway related to Gtk but actually constitutes a hierarchical "graph" of graphical primitives. The "Root" of said graph is the one from which all the others can be reached.

However in the vast majority of applications one normally does also incorporate Gtk widget references in the user data. You can make any user data class that you like, complete with methods for processing it and for manipulating the Gtk widgets.

p.s. also I realize it is very annoying when you don't know what something is supposed to do, so I've attached that **complete** test program. All you have to do is unarchive it and type
```

./test.sh

```
and that should compile and run it so can get dizzy watching fractal triangles twirling round each other and then shrug your shoulders as you wonder what the point of that was ;)

---

### Post by stsp on 2011-02-03
2 years ago I implemented that feature, here it is:
[https://bugzilla.gnome.org/show_bug.cgi?id=573482](https://bugzilla.gnome.org/show_bug.cgi?id=573482)
It doesn't look like the gtkmm maintainer is willing to integrate it, though.

---

### Post by stsp on 2011-02-03
And another related discussion is here:
[http://www.mail-archive.com/gtkmm-list@gnome.org/msg13350.html](http://www.mail-archive.com/gtkmm-list@gnome.org/msg13350.html)

---

### Post by nalin4linux77 on 2012-04-25
Friends I am** Nalin X Linux** (Rocking):guitar:
I am presenting a small class program which use Gtkmm and Glade. And  the cause of why i post this software is that  thees days i was serching  for a sampile (easy) program for gtkmm and i never get any easy program  for beginners!!!!!!!

Finally i made a sample program. and now i am dedicating this  program for beginners of gtkmm with glade. because i have a condition no  one else struggle like me !!!!!! 

What ever else the program is given below 

#include <iostream>
using namespace std;
//including the rocking hederfile gtkmm
**#include <gtkmm.h>**
class rock
{
    Gtk::Window* window;
    Gtk::Label* label;
    Gtk::Button* button;
    //Functions must be public 
    public:
    
    void rock_me()
    {
        label->set_label("Yes I am rocking");
        window->maximize();
        //flush must be used for giving output instantly
        cout<<"Nalin X Linux is now rocking"<<flush;
    }
    //Constructer which will involk automatically when object is created
    rock()
    {
        //Creating builder and giving file called rock.glade which is in same directory
        Glib::RefPtr<Gtk::Builder> builder = Gtk::Builder::create_from_file("rock.glade");
        //Getting widget from glade file 
        builder->get_widget("window",window);
        builder->get_widget("button",button);
        builder->get_widget("label", label);
        // "*this" is a pointer which point to itself
        button->signal_clicked().connect(sigc::mem_fun(*this, &rock::rock_me));
        //Final running 
        Gtk::Main::run(*window);
    } 
};
int main(int argc,char *argv[])
{
    Gtk::Main kit(argc,argv);
    //creating the object called ob for the class rock
    rock ob;
}     
//Program finished hear


Download the atached file called  "rock.glade" and copy it to the same directory where you saved the "rock_gtkmm.cpp"
Open the Terminal <<<<<
Now compile it with :        **  g++ -Wall -o "rock_gtkmm" "rock_gtkmm.cpp"  `pkg-config gtkmm-3.0 --cflags --libs`**
Run it with             :         ** ./rock_gtkmm**:lolflag:

Have a nice day <<<<<<<<<<< Thanks for reading 
by your friend Nalin X Linux :guitar:

---

