---
title: "Gtkmm problem"
date: 2009-09-24
forum: Programming Talk
---

### Post by matmatmat on 2009-09-24
I have this code:
```

#include <libglademm/xml.h>
#include <gtkmm.h>
#include <iostream>


#ifdef ENABLE_NLS
#  include <libintl.h>
#endif


/* For testing propose use the local (not installed) glade file */
/* #define GLADE_FILE PACKAGE_DATA_DIR"/gtk_foobar/glade/gtk_foobar.glade" */
#define GLADE_FILE "gtk_foobar.glade"

Gtk::Window* main_win = 0;

static void on_button_clicked()
{
	std:: cout << "h";
}

   
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
	refXml->get_widget("main_window", main_win);
	if (main_win)
	{
		kit.run(*main_win);
	}
	Gtk::Button* mButton = 0;
	refXml->get_widget("mysuperbutton", mButton);
	if (mButton){
		mButton->signal_clicked().connect( sigc::ptr_fun(on_button_clicked) );
	}
	return 0;
}

```
but when you click the button nothing happens

---

### Post by SledgeHammer_999 on 2009-09-24
Maybe because you have a space between "::" and "cout"? If it isn't a copy/paste typo then the above code shouldn't compile.

correct
```
static void on_button_clicked()
{
	std::cout << "h";
}
```

EDIT:
Ooops sorry. I think the actual proplem is here. You forgot an '&'

```
mButton->signal_clicked().connect( sigc::ptr_fun(&on_button_clicked) );
```

Link about gtkmm signals-->[http://library.gnome.org/devel/gtkmm-tutorial/unstable/sec-connecting-signal-handlers.html.en](http://library.gnome.org/devel/gtkmm-tutorial/unstable/sec-connecting-signal-handlers.html.en)

---

### Post by matmatmat on 2009-09-24
Thanks, but it still doesn't work

---

### Post by SledgeHammer_999 on 2009-09-24
maybe mButton == NULL

---

### Post by matmatmat on 2009-09-24
No, that hasn't worked, thanks though

---

### Post by MadCow108 on 2009-09-24
I can't see a problem (with the included &)
so either the problem is somewhere else (in the glade file)
or its just that the endl is missing in the cout so you don't see the h when the button is clicked because the buffer is never flushed
so try adding a << std::endl (or a std::cout.flush())
then check is mbutton is not null
when it still not works the problem lies in the glade file

---

### Post by matmatmat on 2009-09-24
Must be the glade file:
```

<?xml version="1.0"?>
<glade-interface>
  <!-- interface-requires gtk+ 2.16 -->
  <!-- interface-naming-policy toplevel-contextual -->
  <widget class="GtkWindow" id="main_window">
    <property name="visible">True</property>
    <property name="title" translatable="yes">Hello World!</property>
    <property name="default_width">500</property>
    <property name="default_height">400</property>
    <child>
      <widget class="GtkButton" id="mysuperbutton">
        <property name="label" translatable="yes">button</property>
        <property name="visible">True</property>
        <property name="can_focus">True</property>
        <property name="receives_default">True</property>
        <signal name="clicked" handler="on_button_clicked"/>
      </widget>
    </child>
  </widget>
</glade-interface>

```
c++
```

#include <libglademm/xml.h>
#include <gtkmm.h>
#include <iostream>


#ifdef ENABLE_NLS
#  include <libintl.h>
#endif


/* For testing propose use the local (not installed) glade file */
/* #define GLADE_FILE PACKAGE_DATA_DIR"/gtk_foobar/glade/gtk_foobar.glade" */
#define GLADE_FILE "gtk_foobar.glade"

Gtk::Window* main_win = NULL;

void on_button_clicked()
{
    main_win->hide();
	std::cout << "H" << std::endl;
}


   
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
	refXml->get_widget("main_window", main_win);
	if (main_win)
	{
		kit.run(*main_win);
	}
	Gtk::Button* mButton = NULL;
	refXml->get_widget("mysuperbutton", mButton);
	if (mButton){
		mButton->signal_clicked().connect(sigc::ptr_fun(&on_button_clicked));
	}
	return 0;
}


```

---

### Post by MadCow108 on 2009-09-24
oops strange I didn't see that earlier:
your running the run() function before connecting the signal
move that to the end of main:
```

if (main_win)
	{
		kit.run(*main_win);
	}

```

---

### Post by matmatmat on 2009-09-24
Thanks, that worked! Why's it always simple things...?

---

### Post by SledgeHammer_999 on 2009-09-24
+1 to MadCow108

EDIT:
@matmatmat .run() blocks until main_win is hidden, that's why the signal doesn't get connected.

---

