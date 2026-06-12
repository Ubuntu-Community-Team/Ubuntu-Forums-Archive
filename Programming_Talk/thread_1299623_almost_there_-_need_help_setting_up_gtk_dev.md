---
title: "almost there - need help setting up gtk dev"
date: 2009-10-24
forum: Programming Talk
---

### Post by mikejonesey on 2009-10-24
[SIZE=4][B]Summary
[/B][COLOR=Navy]I want to know how to get gtk+ c++ (gtkmm) and Anjuta working...[/COLOR][/SIZE] 
I get this error when compiling gtk (c++ gtkmm) in anjuta
**/usr/include/gtk-2.0/gtk/gtkcolorsel.h:60: error: &#8216;GtkVBox&#8217; does not name a type**

[SIZE=4][B]Full Details
[/B][/SIZE] I have years of programing experience and would love to get developing some new apps for linux, however i can't seem to get gtk interface working.

(I'm a noob to developing in linux)

So far i have created a wxwidgets c++ test program with a connection to a postgre sql database, works great.
(I had to add a few config options to code::blocks to get this working).

Now I wish to take full advantage of gtk libaries, to do this I was attempting to use gtkmm with code::blocks. This threw many errors and I have added many options to the compiler which resolved some issues but not all. I read in another thread that anjuta was great for making things a little easyer setting up.

So I am now using ajuntu which looks and feels great but i still can't compile gtk.
when compiling gtk in ajuntu; 

[LIST]
[*]i get no messages of missing dependancies (i did when i 1st got it).
[*]I do get 10 errors
[/LIST]
The 10 Errors are as follows;

/usr/include/gtk-2.0/gtk/gtkcolorsel.h:60: error: &#8216;GtkVBox&#8217; does not name a type
/usr/include/gtk-2.0/gtk/gtkcolorsel.h:68: error: &#8216;GtkVBoxClass&#8217; does not name a type
/usr/include/gtk-2.0/gtk/gtkfilechooserwidget.h:46: error: &#8216;GtkVBox&#8217; does not name a type
/usr/include/gtk-2.0/gtk/gtkfilechooserwidget.h:53: error: &#8216;GtkVBoxClass&#8217; does not name a type
/usr/include/gtk-2.0/gtk/gtkfontsel.h:69: error: &#8216;GtkVBox&#8217; does not name a type
/usr/include/gtk-2.0/gtk/gtkfontsel.h:94: error: &#8216;GtkVBoxClass&#8217; does not name a type
/usr/include/gtk-2.0/gtk/gtkgamma.h:63: error: &#8216;GtkVBox&#8217; does not name a type
/usr/include/gtk-2.0/gtk/gtkgamma.h:76: error: &#8216;GtkVBoxClass&#8217; does not name a type
/usr/include/gtk-2.0/gtk/gtkrecentchooserwidget.h:48: error: &#8216;GtkVBox&#8217; does not name a type
/usr/include/gtk-2.0/gtk/gtkrecentchooserwidget.h:55: error: &#8216;GtkVBoxClass&#8217; does not name a type

anyone know if i need to add config options or install somthing else?

thanks

--------------------------------

[B][COLOR=Red]update:
[COLOR=Black]
[/COLOR][/COLOR][/B][COLOR=Red][COLOR=Black]I think i may need to include somthing before htkmm.h?
[/COLOR][/COLOR][COLOR=Red][COLOR=Black]
my code is[B]:

[/B][/COLOR][/COLOR]> 
#include <libglademm/xml.h>
#include <gtkmm.h>
#include <iostream>

#ifdef ENABLE_NLS
#  include <libintl.h>
#endif


/* For testing propose use the local (not installed) glade file */
/* #define GLADE_FILE PACKAGE_DATA_DIR"/gtk_foobar/glade/gtk_foobar.glade" */
#define GLADE_FILE "src/gtk_foobar.glade"
   
int
main (int argc, char *argv[])
{
    Gtk::Main kit(argc, argv);
    
    //Load the Glade file and instiate its widgets:
    Glib::RefPtr<Gnome::Glade::Xml> refXml;
    try
    {
        refXml = Gnome::Glade::Xml::create(GLADE_FILE);
    }
    catch(const Gnome::Glade::XmlError& ex)
    {
        std::cerr << ex.what() << std::endl;
        return 1;
    }
    Gtk::Window* main_win = 0;
    refXml->get_widget("main_window", main_win);
    if (main_win)
    {
        kit.run(*main_win);
    }
    return 0;
}

[COLOR=Red]
update:[/COLOR]

[COLOR=Black]please anyone?[/COLOR]

---

### Post by giuspen on 2009-10-24
Hi Mike,
same as you I started with the idea of Gtkmm (as I like C++) and Anjuta but then, being learning python too thanks to some nautilus python extensions I had to write, I started to appreciate PyGTK and I advice you to take a look to it as it's very fast and powerful tool.
I started with [this tutorial]("http://www.micahcarrick.com/12-24-2007/gtk-glade-tutorial-part-1.html") and I fast improved how you can see with the three applications that I work on (cherrytree, x-tile and nautilus pyextensions, links below).
About using Anjuta I rather advice you [Geany]("http://www.geany.org/"), then Glade with PyGTK.
Cheers,
Giuseppe.

---

### Post by SledgeHammer_999 on 2009-10-25
@mikejonesey

let's say you have named the file with the above source main.cpp
Does it compile with this(in a terminal)?:
```
g++ main.cpp `pkg-config gtkmm-2.4 --libs --cflags` -o test
```

If not, what is the output of the terminal?

---

### Post by mikejonesey on 2009-10-25
> **SledgeHammer_999 said:**
> @mikejonesey

let's say you have named the file with the above source main.cpp
Does it compile with this(in a terminal)?:
```
g++ main.cpp `pkg-config gtkmm-2.4 --libs --cflags` -o test
```If not, what is the output of the terminal?
thanks the out put is:
```

mike@mike-laptop:~/gtk-foobar/src$ g++ main.cc `pkg-config gtkmm-2.4 --libs --cflags` -o test
main.cc:20:28: error: libglademm/xml.h: No such file or directory
In file included from /usr/include/gtk-2.0/gtk/gtk.h:69,
                 from /usr/include/gtkmm-2.4/gtkmm/targetentry.h:30,
                 from /usr/include/gtkmm-2.4/gtkmm/targetlist.h:28,
                 from /usr/include/gtkmm-2.4/gtkmm/widget.h:46,
                 from /usr/include/gtkmm-2.4/gtkmm/container.h:29,
                 from /usr/include/gtkmm-2.4/gtkmm/bin.h:30,
                 from /usr/include/gtkmm-2.4/gtkmm/window.h:32,
                 from /usr/include/gtkmm-2.4/gtkmm/dialog.h:30,
                 from /usr/include/gtkmm-2.4/gtkmm/aboutdialog.h:30,
                 from /usr/include/gtkmm-2.4/gtkmm.h:34,
                 from main.cc:22:
/usr/include/gtk-2.0/gtk/gtkcolorsel.h:60: error: ‘GtkVBox’ does not name a type
/usr/include/gtk-2.0/gtk/gtkcolorsel.h:68: error: ‘GtkVBoxClass’ does not name a type
In file included from /usr/include/gtk-2.0/gtk/gtk.h:89,
                 from /usr/include/gtkmm-2.4/gtkmm/targetentry.h:30,
                 from /usr/include/gtkmm-2.4/gtkmm/targetlist.h:28,
                 from /usr/include/gtkmm-2.4/gtkmm/widget.h:46,
                 from /usr/include/gtkmm-2.4/gtkmm/container.h:29,
                 from /usr/include/gtkmm-2.4/gtkmm/bin.h:30,
                 from /usr/include/gtkmm-2.4/gtkmm/window.h:32,
                 from /usr/include/gtkmm-2.4/gtkmm/dialog.h:30,
                 from /usr/include/gtkmm-2.4/gtkmm/aboutdialog.h:30,
                 from /usr/include/gtkmm-2.4/gtkmm.h:34,
                 from main.cc:22:
/usr/include/gtk-2.0/gtk/gtkfilechooserwidget.h:46: error: ‘GtkVBox’ does not name a type
/usr/include/gtk-2.0/gtk/gtkfilechooserwidget.h:53: error: ‘GtkVBoxClass’ does not name a type
In file included from /usr/include/gtk-2.0/gtk/gtk.h:92,
                 from /usr/include/gtkmm-2.4/gtkmm/targetentry.h:30,
                 from /usr/include/gtkmm-2.4/gtkmm/targetlist.h:28,
                 from /usr/include/gtkmm-2.4/gtkmm/widget.h:46,
                 from /usr/include/gtkmm-2.4/gtkmm/container.h:29,
                 from /usr/include/gtkmm-2.4/gtkmm/bin.h:30,
                 from /usr/include/gtkmm-2.4/gtkmm/window.h:32,
                 from /usr/include/gtkmm-2.4/gtkmm/dialog.h:30,
                 from /usr/include/gtkmm-2.4/gtkmm/aboutdialog.h:30,
                 from /usr/include/gtkmm-2.4/gtkmm.h:34,
                 from main.cc:22:
/usr/include/gtk-2.0/gtk/gtkfontsel.h:69: error: ‘GtkVBox’ does not name a type
/usr/include/gtk-2.0/gtk/gtkfontsel.h:94: error: ‘GtkVBoxClass’ does not name a type
In file included from /usr/include/gtk-2.0/gtk/gtk.h:94,
                 from /usr/include/gtkmm-2.4/gtkmm/targetentry.h:30,
                 from /usr/include/gtkmm-2.4/gtkmm/targetlist.h:28,
                 from /usr/include/gtkmm-2.4/gtkmm/widget.h:46,
                 from /usr/include/gtkmm-2.4/gtkmm/container.h:29,
                 from /usr/include/gtkmm-2.4/gtkmm/bin.h:30,
                 from /usr/include/gtkmm-2.4/gtkmm/window.h:32,
                 from /usr/include/gtkmm-2.4/gtkmm/dialog.h:30,
                 from /usr/include/gtkmm-2.4/gtkmm/aboutdialog.h:30,
                 from /usr/include/gtkmm-2.4/gtkmm.h:34,
                 from main.cc:22:
/usr/include/gtk-2.0/gtk/gtkgamma.h:63: error: ‘GtkVBox’ does not name a type
/usr/include/gtk-2.0/gtk/gtkgamma.h:76: error: ‘GtkVBoxClass’ does not name a type
In file included from /usr/include/gtk-2.0/gtk/gtk.h:152,
                 from /usr/include/gtkmm-2.4/gtkmm/targetentry.h:30,
                 from /usr/include/gtkmm-2.4/gtkmm/targetlist.h:28,
                 from /usr/include/gtkmm-2.4/gtkmm/widget.h:46,
                 from /usr/include/gtkmm-2.4/gtkmm/container.h:29,
                 from /usr/include/gtkmm-2.4/gtkmm/bin.h:30,
                 from /usr/include/gtkmm-2.4/gtkmm/window.h:32,
                 from /usr/include/gtkmm-2.4/gtkmm/dialog.h:30,
                 from /usr/include/gtkmm-2.4/gtkmm/aboutdialog.h:30,
                 from /usr/include/gtkmm-2.4/gtkmm.h:34,
                 from main.cc:22:
/usr/include/gtk-2.0/gtk/gtkrecentchooserwidget.h:48: error: ‘GtkVBox’ does not name a type
/usr/include/gtk-2.0/gtk/gtkrecentchooserwidget.h:55: error: ‘GtkVBoxClass’ does not name a type
main.cc: In function ‘int main(int, char**)’:
main.cc:39: error: ‘Gnome’ was not declared in this scope
main.cc:39: error: template argument 1 is invalid
main.cc:39: error: invalid type in declaration before ‘;’ token
main.cc:42: error: ‘Gnome’ is not a class or namespace
main.cc:44: error: ISO C++ forbids declaration of ‘Gnome’ with no type
main.cc:44: error: expected `)' before ‘::’ token
main.cc:44: error: expected `{' before ‘::’ token
main.cc:44: error: ‘::Glade’ has not been declared
main.cc:44: error: ‘ex’ was not declared in this scope
main.cc:44: error: expected `;' before ‘)’ token
main.cc:50: error: base operand of ‘->’ is not a pointer

```

---

### Post by mikejonesey on 2009-10-25
thanks, but i'd rather go for c++

---

### Post by SledgeHammer_999 on 2009-10-26
It seems that you are missing the dev files. They contain the headers for the libraries. Open Synaptic(or use agt-get) and install **libglademm-2.4-dev** and **libgtkmm-2.4-dev**.

After that give this command in a terminal and it should compile:
```
g++ main.cpp `pkg-config libglademm-2.4 gtkmm-2.4 --libs --cflags` -o test
```

Also I saw your post [here](http://ubuntuforums.org/showthread.php?t=1298328). I will help you set up Code::Blocks if the above command works.

---

### Post by mikejonesey on 2009-10-26
thanks,

but the two packages mentioned above are already installed;

output:
```

mike@mike-laptop:~/gtk-foobar/src$ g++ main.cc `pkg-config libglademm-2.4 gtkmm-2.4 --libs --cflags` -o test
In file included from /usr/include/gtk-2.0/gtk/gtk.h:69,
                 from /usr/include/gtkmm-2.4/gtkmm/targetentry.h:30,
                 from /usr/include/gtkmm-2.4/gtkmm/targetlist.h:28,
                 from /usr/include/gtkmm-2.4/gtkmm/widget.h:46,
                 from /usr/include/gtkmm-2.4/gtkmm/container.h:29,
                 from /usr/include/libglademm-2.4/libglademm/xml.h:28,
                 from main.cc:20:
/usr/include/gtk-2.0/gtk/gtkcolorsel.h:60: error: &#8216;GtkVBox&#8217; does not name a type
/usr/include/gtk-2.0/gtk/gtkcolorsel.h:68: error: &#8216;GtkVBoxClass&#8217; does not name a type
In file included from /usr/include/gtk-2.0/gtk/gtk.h:89,
                 from /usr/include/gtkmm-2.4/gtkmm/targetentry.h:30,
                 from /usr/include/gtkmm-2.4/gtkmm/targetlist.h:28,
                 from /usr/include/gtkmm-2.4/gtkmm/widget.h:46,
                 from /usr/include/gtkmm-2.4/gtkmm/container.h:29,
                 from /usr/include/libglademm-2.4/libglademm/xml.h:28,
                 from main.cc:20:
/usr/include/gtk-2.0/gtk/gtkfilechooserwidget.h:46: error: &#8216;GtkVBox&#8217; does not name a type
/usr/include/gtk-2.0/gtk/gtkfilechooserwidget.h:53: error: &#8216;GtkVBoxClass&#8217; does not name a type
In file included from /usr/include/gtk-2.0/gtk/gtk.h:92,
                 from /usr/include/gtkmm-2.4/gtkmm/targetentry.h:30,
                 from /usr/include/gtkmm-2.4/gtkmm/targetlist.h:28,
                 from /usr/include/gtkmm-2.4/gtkmm/widget.h:46,
                 from /usr/include/gtkmm-2.4/gtkmm/container.h:29,
                 from /usr/include/libglademm-2.4/libglademm/xml.h:28,
                 from main.cc:20:
/usr/include/gtk-2.0/gtk/gtkfontsel.h:69: error: &#8216;GtkVBox&#8217; does not name a type
/usr/include/gtk-2.0/gtk/gtkfontsel.h:94: error: &#8216;GtkVBoxClass&#8217; does not name a type
In file included from /usr/include/gtk-2.0/gtk/gtk.h:94,
                 from /usr/include/gtkmm-2.4/gtkmm/targetentry.h:30,
                 from /usr/include/gtkmm-2.4/gtkmm/targetlist.h:28,
                 from /usr/include/gtkmm-2.4/gtkmm/widget.h:46,
                 from /usr/include/gtkmm-2.4/gtkmm/container.h:29,
                 from /usr/include/libglademm-2.4/libglademm/xml.h:28,
                 from main.cc:20:
/usr/include/gtk-2.0/gtk/gtkgamma.h:63: error: &#8216;GtkVBox&#8217; does not name a type
/usr/include/gtk-2.0/gtk/gtkgamma.h:76: error: &#8216;GtkVBoxClass&#8217; does not name a type
In file included from /usr/include/gtk-2.0/gtk/gtk.h:152,
                 from /usr/include/gtkmm-2.4/gtkmm/targetentry.h:30,
                 from /usr/include/gtkmm-2.4/gtkmm/targetlist.h:28,
                 from /usr/include/gtkmm-2.4/gtkmm/widget.h:46,
                 from /usr/include/gtkmm-2.4/gtkmm/container.h:29,
                 from /usr/include/libglademm-2.4/libglademm/xml.h:28,
                 from main.cc:20:
/usr/include/gtk-2.0/gtk/gtkrecentchooserwidget.h:48: error: &#8216;GtkVBox&#8217; does not name a type
/usr/include/gtk-2.0/gtk/gtkrecentchooserwidget.h:55: error: &#8216;GtkVBoxClass&#8217; does not name a type

```

and to check file does exist:
```

mike@mike-laptop:~/gtk-foobar/src$ locate libglademm/xml.h
/usr/include/libglademm-2.4/libglademm/xml.h

```

---

### Post by SledgeHammer_999 on 2009-10-26
Hmmm I don't know what's wrong. Let's try to compile a simple gtkmm program without using glademm. Put this in main.cpp:
[php]
#include <gtkmm/button.h>
#include <gtkmm/window.h>
#include <gtkmm/main.h>
#include <iostream>

class HelloWorld : public Gtk::Window
{

public:
  HelloWorld();
  virtual ~HelloWorld();

protected:
  //Signal handlers:
  void on_button_clicked();

  //Member widgets:
  Gtk::Button m_button;
};

HelloWorld::HelloWorld()
: m_button("Hello World")   // creates a new button with label "Hello World".
{
  // Sets the border width of the window.
  set_border_width(10);

  // When the button receives the "clicked" signal, it will call the
  // on_button_clicked() method defined below.
  m_button.signal_clicked().connect(sigc::mem_fun(*this,
              &HelloWorld::on_button_clicked));

  // This packs the button into the Window (a container).
  add(m_button);

  // The final step is to display this newly created widget...
  m_button.show();
}

HelloWorld::~HelloWorld()
{
}

void HelloWorld::on_button_clicked()
{
  std::cout << "Hello World" << std::endl;
}

int main (int argc, char *argv[])
{
  Gtk::Main kit(argc, argv);

  HelloWorld helloworld;
  //Shows the window and returns when it is closed.
  Gtk::Main::run(helloworld);

  return 0;
}

[/php]

And compile with:
```
g++ main.cpp `pkg-config gtkmm-2.4 --libs --cflags` -o test
```

---

### Post by mikejonesey on 2009-10-26
:(

```

mike@mike-laptop:~$ mkdir newtest
mike@mike-laptop:~$ cd newtest
mike@mike-laptop:~/newtest$ dir
mike@mike-laptop:~/newtest$ gedit main.cpp
mike@mike-laptop:~/newtest$ g++ main.cpp `pkg-config gtkmm-2.4 --libs --cflags` -o test
In file included from /usr/include/gtk-2.0/gtk/gtk.h:69,
                 from /usr/include/gtkmm-2.4/gtkmm/targetentry.h:30,
                 from /usr/include/gtkmm-2.4/gtkmm/targetlist.h:28,
                 from /usr/include/gtkmm-2.4/gtkmm/widget.h:46,
                 from /usr/include/gtkmm-2.4/gtkmm/container.h:29,
                 from /usr/include/gtkmm-2.4/gtkmm/bin.h:30,
                 from /usr/include/gtkmm-2.4/gtkmm/button.h:30,
                 from main.cpp:1:
/usr/include/gtk-2.0/gtk/gtkcolorsel.h:60: error: &#8216;GtkVBox&#8217; does not name a type
/usr/include/gtk-2.0/gtk/gtkcolorsel.h:68: error: &#8216;GtkVBoxClass&#8217; does not name a type
In file included from /usr/include/gtk-2.0/gtk/gtk.h:89,
                 from /usr/include/gtkmm-2.4/gtkmm/targetentry.h:30,
                 from /usr/include/gtkmm-2.4/gtkmm/targetlist.h:28,
                 from /usr/include/gtkmm-2.4/gtkmm/widget.h:46,
                 from /usr/include/gtkmm-2.4/gtkmm/container.h:29,
                 from /usr/include/gtkmm-2.4/gtkmm/bin.h:30,
                 from /usr/include/gtkmm-2.4/gtkmm/button.h:30,
                 from main.cpp:1:
/usr/include/gtk-2.0/gtk/gtkfilechooserwidget.h:46: error: &#8216;GtkVBox&#8217; does not name a type
/usr/include/gtk-2.0/gtk/gtkfilechooserwidget.h:53: error: &#8216;GtkVBoxClass&#8217; does not name a type
In file included from /usr/include/gtk-2.0/gtk/gtk.h:92,
                 from /usr/include/gtkmm-2.4/gtkmm/targetentry.h:30,
                 from /usr/include/gtkmm-2.4/gtkmm/targetlist.h:28,
                 from /usr/include/gtkmm-2.4/gtkmm/widget.h:46,
                 from /usr/include/gtkmm-2.4/gtkmm/container.h:29,
                 from /usr/include/gtkmm-2.4/gtkmm/bin.h:30,
                 from /usr/include/gtkmm-2.4/gtkmm/button.h:30,
                 from main.cpp:1:
/usr/include/gtk-2.0/gtk/gtkfontsel.h:69: error: &#8216;GtkVBox&#8217; does not name a type
/usr/include/gtk-2.0/gtk/gtkfontsel.h:94: error: &#8216;GtkVBoxClass&#8217; does not name a type
In file included from /usr/include/gtk-2.0/gtk/gtk.h:94,
                 from /usr/include/gtkmm-2.4/gtkmm/targetentry.h:30,
                 from /usr/include/gtkmm-2.4/gtkmm/targetlist.h:28,
                 from /usr/include/gtkmm-2.4/gtkmm/widget.h:46,
                 from /usr/include/gtkmm-2.4/gtkmm/container.h:29,
                 from /usr/include/gtkmm-2.4/gtkmm/bin.h:30,
                 from /usr/include/gtkmm-2.4/gtkmm/button.h:30,
                 from main.cpp:1:
/usr/include/gtk-2.0/gtk/gtkgamma.h:63: error: &#8216;GtkVBox&#8217; does not name a type
/usr/include/gtk-2.0/gtk/gtkgamma.h:76: error: &#8216;GtkVBoxClass&#8217; does not name a type
In file included from /usr/include/gtk-2.0/gtk/gtk.h:152,
                 from /usr/include/gtkmm-2.4/gtkmm/targetentry.h:30,
                 from /usr/include/gtkmm-2.4/gtkmm/targetlist.h:28,
                 from /usr/include/gtkmm-2.4/gtkmm/widget.h:46,
                 from /usr/include/gtkmm-2.4/gtkmm/container.h:29,
                 from /usr/include/gtkmm-2.4/gtkmm/bin.h:30,
                 from /usr/include/gtkmm-2.4/gtkmm/button.h:30,
                 from main.cpp:1:
/usr/include/gtk-2.0/gtk/gtkrecentchooserwidget.h:48: error: &#8216;GtkVBox&#8217; does not name a type
/usr/include/gtk-2.0/gtk/gtkrecentchooserwidget.h:55: error: &#8216;GtkVBoxClass&#8217; does not name a type
mike@mike-laptop:~/newtest$ 

```

---

### Post by SledgeHammer_999 on 2009-10-26
It compiles on my computer and should on yours. What version of ubuntu do you use?
Reinstall the libgtkmm-2.4-dev package. Maybe it will solve the problems.

---

### Post by mikejonesey on 2009-10-26
i'm on jaunty jokealope, trying to reinstall libgtkmm-2.4-dev now

ps many thanks for your time

---

### Post by mikejonesey on 2009-10-26
no luck :(

what do you have in gtkcolorsel.h on line 60;

i have;

```

GtkVBox parent_instance;

```

from

```

struct _GtkColorSelection
{
  GtkVBox parent_instance;

  /* < private_data > */
  gpointer GSEAL (private_data);
};

```

i think there is somthing installed on your machine that is not on mine! :)

---

### Post by SledgeHammer_999 on 2009-10-26
I have exactly the same thing! This is weird! I suppose you have downloaded all updates, right?

Maybe you have "played around" on your machine and messed something up. Or maybe it is a borked OS install... I don't know if you can, but wait till 29 October and install Karmic from scratch.

---

### Post by mikejonesey on 2009-10-26
yea i guess... hate waiting... want to make some crm software :)

---

### Post by SledgeHammer_999 on 2009-10-26
Although it should be pulled automatically when you installed libgtkmm, do you have libgtk2.0-dev installed?

---

### Post by mikejonesey on 2009-10-26
> **SledgeHammer_999 said:**
> Although it should be pulled automatically when you installed libgtkmm, do you have libgtk2.0-dev installed?

libgtk2.0-dev is already the newest version.

:)

---

### Post by mikejonesey on 2009-10-31
don't know what the problem was but after upgrading to ubuntu 9.10 all works. :)

---

### Post by SledgeHammer_999 on 2009-10-31
probably something was borked :p

If you need help to set up Code::blocks just ask.

---

