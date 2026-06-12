---
title: "Using a number with an entry widget in gtkmm"
date: 2010-10-28
forum: Programming Talk
---

### Post by LuxVan on 2010-10-28
Hi you all!
I have a question: I do not know how to use a number with an entry widget in gtkmm.
I am a c++/gtkmm beginner programmer.
I would like to insert a number in an entry and show it in a label, after clicking a button..
Can you help me?
Sorry for my english!:popcorn:

---

### Post by SledgeHammer_999 on 2010-10-28
In gtkmm, Gtk::Labels and Gtk:Entry take a Glib::ustring as an argument. So your question should be: "How do I convert a number(numerical value) to a Glib::ustring(string value)?"

For the answer look at the Glib::ustring::compose() functions here->[http://library.gnome.org/devel/glibmm/unstable/classGlib_1_1ustring.html#af4931a2830a2a41568ea3330870e8358](http://library.gnome.org/devel/glibmm/unstable/classGlib_1_1ustring.html#af4931a2830a2a41568ea3330870e8358)

---

### Post by LuxVan on 2010-10-29
Ok.
Can you help me to understand how to work glib? Where can I read something?
I have wrote that:
```
void window::somma_button()
{
   stringa = entry1.get_text();
   a=ustring::compose("%d",stringa);
   entry2.set_text(a);
}
```
But do not work....

---

### Post by worksofcraft on 2010-10-29
Hey Luxvan here I wrote this specially to get you started instead of referring to long totorials.

First copy this into a file called spintst.cpp then use the compile command given as first comment to make it into an app called a.out.
[php]
// Compile: g++ spintst.cpp `pkg-config gtkmm-2.4 --cflags --libs`
#include <gtkmm.h>

// pointers to all the widgets
struct Widgets {
	Gtk::Label *pLabel1;
	Gtk::SpinButton *pSpin1;
	Gtk::Button *pBut1;
	Gtk::Window *pWin1;

	// constructor obtains pointers to the widgets made by builder
	Widgets(Glib::RefPtr<Gtk::Builder> builder) {
		builder->get_widget("spinbutton1", pSpin1);
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
// http://library.gnome.org/devel/gtkmm/unstable/classGtk_1_1SpinButton.html
void Widgets::on_button1_clicked() {
	// create a text string to display
	char aBuf[50];
	snprintf(aBuf, sizeof(aBuf), "spin=%d", pSpin1->get_value_as_int());
	// display the text string in the label
	pLabel1->set_text(aBuf);
}

// program entry point
int main(int argc, char *argv[]) {
	// process typical command line arguments
	Gtk::Main kit(argc, argv);

	// instantiate the widgets as defined by glade's XML file
	Widgets allTheWidgets(
		Gtk::Builder::create_from_file("spintst.glade")
	);
	// then process all the user input
	return allTheWidgets.run();
}
[/php]

Then you need also this to define your user interface: copy it into a file called "spintst.glade" in the same folder.
```

<?xml version="1.0"?>
<interface>
  <requires lib="gtk+" version="2.16"/>
  <!-- interface-naming-policy project-wide -->
  <object class="GtkWindow" id="window1">
    <property name="default_width">200</property>
    <child>
      <object class="GtkVBox" id="vbox1">
        <property name="visible">True</property>
        <child>
          <object class="GtkButton" id="button1">
            <property name="label" translatable="yes">button</property>
            <property name="visible">True</property>
            <property name="can_focus">True</property>
            <property name="receives_default">True</property>
          </object>
          <packing>
            <property name="position">0</property>
          </packing>
        </child>
        <child>
          <object class="GtkSpinButton" id="spinbutton1">
            <property name="visible">True</property>
            <property name="can_focus">True</property>
            <property name="invisible_char">&#x25CF;</property>
            <property name="adjustment">adjustment1</property>
          </object>
          <packing>
            <property name="position">1</property>
          </packing>
        </child>
        <child>
          <object class="GtkLabel" id="label1">
            <property name="visible">True</property>
            <property name="label" translatable="yes">label</property>
          </object>
          <packing>
            <property name="position">2</property>
          </packing>
        </child>
      </object>
    </child>
  </object>
  <object class="GtkAdjustment" id="adjustment1">
    <property name="upper">100</property>
    <property name="step_increment">1</property>
    <property name="page_increment">10</property>
    <property name="page_size">10</property>
  </object>
</interface>

```

Glade files can be created and edited with the glade gui designer which is much easier than doing coding it yourself ;)

---

### Post by worksofcraft on 2010-10-30
oh I forgot to say... you can then just click on the a.out icon, or type ./a.out at command line in appropriate working directory and you should get display like below. You enter a number then click the button and it gets displayed on the label.

I know it looks a bit naff but I just let glade fill in all the default values so you can easily recreate and experiment to make it look more professional ;)

p.s. do say if no good for you because otherwise we can't help.

---

### Post by LuxVan on 2010-10-30
Just another question, in your example you take a number from spinbox, but I would like to take a number from an entry...and the entry widget do not has get_value_as_int() member...
I think that I should convert a string in a number, but I do not understand how I should do it....

---

### Post by fallenshadow on 2010-10-30
worksofcraft nice tutorial code! :)

Even for myself its neat to learn how to do such things with gtkmm!

---

### Post by worksofcraft on 2010-10-30
> **LuxVan said:**
> Just another question, in your example you take a number from spinbox, but I would like to take a number from an entry...and the entry widget do not has get_value_as_int() member...
I think that I should convert a string in a number, but I do not understand how I should do it....

Ah OK, instead Gtk::Entry has:
[php]
Glib::ustring 	get_text () const
[/php]

However to output to a label you must supply an old "C" style char *. For this you can use the Glib::ustring::c_str method. Something like this might work:
[php]
void window::somma_button()
{
   Glib::ustring stringa = entry1.get_text();
   entry2.set_text(stringa.c_str());
}
[/php]

---

### Post by worksofcraft on 2010-10-31
> **fallenshadow said:**
> worksofcraft nice tutorial code! :)

Even for myself its neat to learn how to do such things with gtkmm!

^^ TY :)
I like explaining things. Even had a job as tutor once but they usually require some kind of qualifications for those kind of jobs :(

p.s. lots of people get to this forum from search engines so useful posts are beneficial and attract more good contributors :)

---

### Post by LuxVan on 2010-11-13
> **worksofcraft said:**
> Ah OK, instead Gtk::Entry has:
[php]
Glib::ustring 	get_text () const
[/php]

However to output to a label you must supply an old "C" style char *. For this you can use the Glib::ustring::c_str method. Something like this might work:
[php]
void window::somma_button()
{
   Glib::ustring stringa = entry1.get_text();
   entry2.set_text(stringa.c_str());
}
[/php]
But the number is stringa?
I would like to add this: stringa + 5. How I can do?

---

### Post by SledgeHammer_999 on 2010-11-13
@LuxVan since you're a C++ beginner I'll explain it again. In C++ you can't just "add" a string and an int variable. Look at this:

[php]
Glib::ustring str = "text"; //str is a string VARIABLE
int num = 5; //num is an integer VARIABLE
Glib::ustring str_num = "5"; //str_num is a string VARIABLE.

/*the following don't make sense on their own.*/
"5" //this is a string CONSTANT
5 //this is an integer CONSTANT

/*Notice the difference: "" marks */
[/php]

So when you try to do "stringa + 5" you're adding a string variable and an integer constant. The compiler can't compile this. There are 2 ways to achieve what you want:

1. Convert the integer constant to a string constant.
[php]
Glib::ustring new_string = stringa + "5";
[/php]
2. Use the appropriate Glib::ustring::compose() function to convert ANY **numeric** constant/variable to a string.
[php]
Glib::ustring new_string = Glib::ustring::compose("%1%2", stringa, 5);

//another example with an integer variable
int num = 666;
Glib::ustring stringa = " the number of the Beast!";
Glib::ustring new_string = Glib::ustring::compose("%1%2", num, stringa);
[/php]

---

### Post by LuxVan on 2010-11-14
> **SledgeHammer_999 said:**
> @LuxVan since you're a C++ beginner I'll explain it again. In C++ you can't just "add" a string and an int variable. Look at this:

[php]
Glib::ustring str = "text"; //str is a string VARIABLE
int num = 5; //num is an integer VARIABLE
Glib::ustring str_num = "5"; //str_num is a string VARIABLE.

/*the following don't make sense on their own.*/
"5" //this is a string CONSTANT
5 //this is an integer CONSTANT

/*Notice the difference: "" marks */
[/php]

So when you try to do "stringa + 5" you're adding a string variable and an integer constant. The compiler can't compile this. There are 2 ways to achieve what you want:

1. Convert the integer constant to a string constant.
[php]
Glib::ustring new_string = stringa + "5";
[/php]
2. Use the appropriate Glib::ustring::compose() function to convert ANY **numeric** constant/variable to a string.
[php]
Glib::ustring new_string = Glib::ustring::compose("%1%2", stringa, 5);

//another example with an integer variable
int num = 666;
Glib::ustring stringa = " the number of the Beast!";
Glib::ustring new_string Glib::ustring::compose("%1%2", num, stringa);
[/php]
Many thanks...I have solved using sstream...it is an error?
Maybe is better to use Glib?
I do not speak in english very well, so, I do not understand always that you tell me...](*,):-s

---

### Post by SledgeHammer_999 on 2010-11-14
Using stringstream is ok too.
If you use std::string instead of Glib::ustring then stringstream is the only viable solution.

EDIT: I edited my code. I forgot something on the last line.

---

