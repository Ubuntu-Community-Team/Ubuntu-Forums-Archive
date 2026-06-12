---
title: "gtkmm connect glade signals"
date: 2010-08-12
forum: Programming Talk
---

### Post by worksofcraft on 2010-08-12
I know how to laboriously connect each handler to each widget signal, but in C a single call to gtk_builder_connect_signals() connects ALL the signal handlers that were specified in Glade.

I would much appreciate if someone can help me do this in C++ now :confused: Here is my simplified code so far.
```

#include <gtkmm.h>

G_MODULE_EXPORT void on_button1_clicked(
	GtkButton *button,
	gpointer data
) {
	printf("button1_clicked\n");
}

int main(int argc, char *argv[]) {
	Gtk::Main kit(argc, argv);

	// instantiate the widgets as defined by glade's XML file
	Glib::RefPtr<Gtk::Builder> builder = Gtk::Builder::create_from_file("HelloAgain.glade");

	// run with reference to the top level window
	Gtk::Window *pWin = NULL;
	builder->get_widget("window1", pWin);
	Gtk::Main::run(*pWin);
	return 0;
}

```

---

### Post by worksofcraft on 2010-08-13
Here follows my glade file, (although it is most intelligibly  viewed with Glade obviously).

What you can see here is the specification of <signal name="clicked" handler="on_button1_clicked"/> for button1 (yes, for sake of simplicity I kept as much default values as I could)

and what you can't see, because I took it out deliberately, is connecting window1 destroy signal to gtk_main_quit() but guess what... when you destroy window1 it mysteriously still quits anyway :roll:

I know the object oriented Python interface works a treat and has great tutorials and whatever, but I want to know how to use it properly in C++ now rather than keep using the C interface with my own home brew wrappers. :-$

```

<?xml version="1.0"?>
<interface>
  <requires lib="gtk+" version="2.16"/>
  <!-- interface-naming-policy project-wide -->
  <object class="GtkWindow" id="window1">
    <property name="visible">True</property>
    <child>
      <object class="GtkVBox" id="vbox1">
        <property name="visible">True</property>
        <child>
          <object class="GtkButton" id="button1">
            <property name="label" translatable="yes">button</property>
            <property name="visible">True</property>
            <property name="can_focus">True</property>
            <property name="receives_default">True</property>
            <signal name="clicked" handler="on_button1_clicked"/>
          </object>
          <packing>
            <property name="position">0</property>
          </packing>
        </child>
        <child>
          <object class="GtkLabel" id="label1">
            <property name="visible">True</property>
            <property name="label" translatable="yes">label</property>
          </object>
          <packing>
            <property name="position">1</property>
          </packing>
        </child>
      </object>
    </child>
  </object>
</interface>

```

---

### Post by worksofcraft on 2010-08-13
Oh well I did see quite a lot of posts in different places on the web asking for a simple C++ flavored "Hello World", so for those you don't mind having to connect each signal explicitly here is one that works (beware - error handling elided for brevity):

```

// g++ HelloAgain.cc `pkg-config gtkmm-2.4 --cflags --libs`
#include <gtkmm.h>

// pointers to all the widgets
struct Widgets {
	Gtk::Label *pLabel1;
	Gtk::Button *pBut1;
	Gtk::Window *pWin1;

	// constructor obtains pointers to the widgets made by builder
	Widgets(Glib::RefPtr<Gtk::Builder> builder) {
		builder->get_widget("button1", pBut1);
		builder->get_widget("label1", pLabel1);
		builder->get_widget("window1", pWin1);
	}

	// declare our signal handler
	void on_button1_clicked();

	int run() {
		// connect a handler to button1 clicked signal 
		pBut1->signal_clicked().connect(
			sigc::mem_fun(this, &Widgets::on_button1_clicked)
		);

		// exit when *pWin1 closes
		Gtk::Main::run(*pWin1);
		return EXIT_SUCCESS; // error handling elided
	}
};

// signal handler for button click
void Widgets::on_button1_clicked() {
	printf("button1_clicked\n"); // a diagnostic message
	pLabel1->set_text("Have a nice day!");
}

// program entry point
int main(int argc, char *argv[]) {
	// process typical command line arguments
	Gtk::Main kit(argc, argv);

	// the one and only genuine K&R original Hello World we evolved from
	printf("Hello World!\n");

	// instantiate the widgets as defined by glade's XML file
	Widgets allTheWidgets(
		Gtk::Builder::create_from_file("HelloAgain.glade")
	);
	// then run it's GUI application
	return allTheWidgets.run();
}

```

---

### Post by milindaaruna on 2012-05-22
See [this]("http://stackoverflow.com/questions/4098636/im-missing-something-obvious-with-glade-gtkbuilder-and-connecting-signals-help")  post, this will give you the answer for your problem. the answer provided by **ptomato** is working for me. (Thanks ptomato!!!)

---

