---
title: "When loading a custom widget with Gtk::Builder it is invisible"
date: 2010-04-18
forum: Programming Talk
---

### Post by mazzzterZ on 2010-04-18
Hi. I'm writing a program for course project and I decided to learn in meantime how to create custom widget and then load them and to make my properties appear in glade. For now nooo luck with both of them. But the more important problem is that my widget is invisible.

My custom widget is in dynamic library and here is its' source and header:


area.h
[PHP]#include <iostream>
#include <gtkmm/notebook.h>
#include <gtkmm/builder.h>

class Area : public Gtk::Notebook {
public:
	Area(BaseObjectType* cobject, const Glib::RefPtr<Gtk::Builder>& refBuilder=Gtk::Builder::create());
	Area();
	~Area();
private:
	Glib::Property<int> integer;
	Glib::Property<double> dnumber;
	Glib::Property<bool> boolean;
	Glib::Property<Glib::ustring> string;

	Glib::RefPtr<Gdk::Window> refGdkWindow;
	int m_scale;
protected:
	//Overrides:
	virtual void on_size_request(Gtk::Requisition* requisition);
	virtual void on_size_allocate(Gtk::Allocation& allocation);
	virtual void on_map();
	virtual void on_unmap();
	virtual void on_realize();
	virtual void on_unrealize();
	virtual bool on_expose_event(GdkEventExpose* event);
private:
	void init();
	void construct();
	void property_changed();
};[/PHP]



area.cpp
[PHP]#include "area.h"
#include <cairomm/cairomm.h>
#include <gtkmm.h>

Area::Area(BaseObjectType* cobject, const Glib::RefPtr<Gtk::Builder>& refBuilder) :
	//The GType name will actually be gtkmm__CustomObject__area
	Glib::ObjectBase("Area"),
	Gtk::Notebook(cobject),
	integer(*this, "test1", 5),
	dnumber(*this, "test3", 12.03),
	boolean(*this, "test4", true),
	string(*this, "test5", "This is string")
{
	construct();
	init();
}

Area::Area() :
	Glib::ObjectBase("Area"),
	Gtk::Notebook(),
	integer(*this, "test1", 5),
	dnumber(*this, "test3", 12.03),
	boolean(*this, "test4", true),
	string(*this, "test5", "This is string")
{
	init();
}

Area::~Area() {
}

void Area::init() {
        ///!!! I tried connecting a signal when a property change but it's never called
	integer.get_proxy().signal_changed().connect(sigc::mem_fun(*this,&Area::property_changed));
	std::cout << "Number: " << integer.get_value() << std::endl;
	std::cout << "Number of pages: " << get_n_pages() << std::endl;
	set_show_tabs(true);
	set_show_border(true);
	show_all_children();
	show_all();
}

void Area::construct() {
	set_flags(Gtk::NO_WINDOW);

	//This shows the GType name, which must be used in the RC file.
	std::cout << "GType name: " << G_OBJECT_TYPE_NAME(gobj()) << std::endl;

	//This show that the GType still derives from GtkWidget:
	//std::cout << "Gtype is a GtkWidget?:" << GTK_IS_WIDGET(gobj()) << std::endl;

	//Install a style so that an aspect of this widget may be themed via an RC file:
	gtk_widget_class_install_style_property(GTK_WIDGET_CLASS(
															G_OBJECT_GET_CLASS(gobj())),
															g_param_spec_int("example_scale",
																	"Scale of Example Drawing",
																	"The scale to use when drawing. This is just a silly example.",
																	G_MININT,
																	G_MAXINT,
																	0,
																	G_PARAM_READABLE)
															);

	  gtk_rc_parse("custom_gtkrc");
}

void Area::property_changed() {
	std::cout << "New value is: " << integer.get_value() << std::endl;
}

void Area::on_size_request(Gtk::Requisition* requisition) {
	//Initialize the output parameter:
	*requisition = Gtk::Requisition();
}

void Area::on_size_allocate(Gtk::Allocation& allocation)
{
	//Do something with the space that we have actually been given:
	//(We will not be given heights or widths less than we have requested, though
	//we might get more)

	//Use the offered allocation for this container:
	set_allocation(allocation);
}

void Area::on_map() {
	//Call base class:
	Gtk::Notebook::on_map();
}

void Area::on_unmap() {
	//Call base class:
	Gtk::Notebook::on_unmap();
}

void Area::on_realize() {
	//Call base class:
	Gtk::Notebook::on_realize();
}

void Area::on_unrealize() {

	//Call base class:
	Gtk::Notebook::on_unrealize();
}

bool Area::on_expose_event(GdkEventExpose* event) {
	return true;
}[/PHP]


Here is the catalog file:
[PHP]<glade-catalog name="widgets" library="widgets" depends="gtk+" domain="glade" language="C++">

	<init-function>catalog_init</init-function>
	
	<glade-widget-classes>
		<glade-widget-class name="gtkmm__CustomObject_Area" generic-name="myarea" title="Area">
			<post-create-function>area_postcreate</post-create-function>
			<properties>
				<property name="TEST1" id="test1" save="True" />
				<property name="TEST3" id="test3" save="True" />
				<property name="TEST4" id="test4" save="True" />
				<property name="TEST5" id="test5" save="True" />
			</properties>
 		</glade-widget-class>
	</glade-widget-classes>
	
	<glade-widget-group name="widgets" title="Widgets">
	    <glade-widget-class-ref name="gtkmm__CustomObject_Area"/>
	</glade-widget-group>
	
</glade-catalog>[/PHP]



Here are some functions need to load my widget in glade:
widget.cpp
[PHP]#include "area.h"
#include <gtkmm/main.h>
#include <glibmm/wrap.h>


void area_init() {
	std::cout << "Inside AREA_INIT function !" << std::endl;
}

// ---------------------------------------------------------
// wrap a GtkNotebook* GObject "upward" to a Area*
static Glib::ObjectBase* area_wrap_new(GObject* o) {
	std::cout << "Inside AREA_WRAP_NEW function !" << std::endl;
//	return Gtk::manage(new Area((GtkNotebook*)(o)));
	return Gtk::manage(new Area());
}

// ---------------------------------------------------------
// get the GType of Area. if not yet registered, do it now
GType area_get_type() {
	std::cout << "Inside AREA_GET_TYPE function !" << std::endl;
	static GType gtype = 0;

	if (!gtype) {
		Area* dummy = new Area();
		gtype = G_OBJECT_TYPE(dummy->gobj());
		delete( dummy );

		Glib::wrap_register(gtype, &area_wrap_new);
	}

	return gtype;
}

// ---------------------------------------------------------
// use this as an init-function in the corresponding catalog file
extern "C" void catalog_init(void) {
	std::cout << "Inside CATALOG_INIT function !" << std::endl;
	Gtk::Main::init_gtkmm_internals();
	area_get_type();
}

// ---------------------------------------------------------
// glade has it's own idea of what the *_get_type() - function should be called
extern "C" GType gtkmm___custom_object__area_get_type(void) {
	return area_get_type();
}

extern "C" GtkNotebook* gtkmm___custom_object__area_new(void) {
	return manage(new Area())->gobj();
}

// ---------------------------------------------------------
// use this as a postcreate-function in the corresponding catalog file, or else
// glade will only show the base widget in it's interface designer
extern "C" void area_postcreate(GObject *object, int reason) {
	std::cout << "Inside AREA_POSTCREATE function !" << std::endl;
}

extern "C" GtkNotebook* area_new() {
	std::cout << "Inside AREA_NEW function !" << std::endl;
	return manage(new Area())->gobj();
}[/PHP]

From these files I compile my dynamic library and for now there is no problem.
Here's the source for my main window that I load and show:

main_form.h
[PHP]#include <gtkmm/window.h>
#include <gtkmm/builder.h>
#include <gtkmm/actiongroup.h>
#include <gtkmm/uimanager.h>

class SDWindow : public Gtk::Window {
private:
	Glib::RefPtr<Gtk::Builder> builder;
	Glib::RefPtr<Gtk::ActionGroup> actionGroup;
	Glib::RefPtr<Gtk::UIManager> UIManager;

public:
	SDWindow();
	~SDWindow();
	void init();
	void on_menu_file_new_selected();
	void on_menu_file_exit_selected();
	void on_menu_action_play_selected();
	void on_menu_action_stop_selected();
	void on_menu_options_configure_selected();
};[/PHP]

main_form.cpp
[PHP]#include "main_form.h"
#include <iostream>
#include <gtkmm/stock.h>
#include <gtkmm/action.h>
#include <gtkmm/box.h>
#include <gtkmm/main.h>
#include <gtkmm.h>
#include "area.h"

SDWindow::SDWindow() {

	//Configure the main window
	set_title("SD - Shape Draw");
    set_default_size(1024, 768);
    set_border_width(3);
    set_position(Gtk::WIN_POS_CENTER_ALWAYS);

    ///!!! I have to call the constructor of Area before I
    ///!!! try to load the glade file.
    ///!!! If I don't do that it throws an exception:
    ///!!! BuilderError: Invalid object type `gtkmm__CustomObject_Area'
    ///!!! If someone knows how to make Gtk::Builder to call this constructor please tell me.
    Area test;
	//Load the Gtk::Builder file
	try {
		builder = Gtk::Builder::create_from_file("./forms/main_form.ui", "BoxedContainer");
	} catch(const Glib::FileError& ex) {
		std::cerr << "FileError: " << ex.what() << std::endl;
	} catch(const Gtk::BuilderError& ex) {
		std::cerr << "BuilderError: " << ex.what() << std::endl;
	}

	Area* a;
	builder->get_widget_derived("myarea", a);
	a->show();

	//Load the menu
	actionGroup = Gtk::ActionGroup::create();
	UIManager = Gtk::UIManager::create();

}

SDWindow::~SDWindow() { }

void test() { }

void SDWindow::init() {

	/* Creating the menu and connecting signals here */


	show_all();
}


void SDWindow::on_menu_file_new_selected() {
}

void SDWindow::on_menu_file_exit_selected() {
	Gtk::Main::quit();
}

void SDWindow::on_menu_action_play_selected() {
}

void SDWindow::on_menu_action_stop_selected() {
}

void SDWindow::on_menu_options_configure_selected() {
}[/PHP]

That's all. The main problem is that when I start the application my custom Notebook widget doesn't show. I tried putting things in it from glade but no luck it's still invisible. I noticed that although it's invisible it knows how many tabs there are in it. I tried the methods show_all(), show_all_children() and in the glade file it's not set as true: "No Show All". So I see no reason why it's hidden.

Since I created a thread I'll ask about my other two problems that aren't important but I think they are good to know.
First is that before I load the glade file I have to call the constructor by creating an object of my problematic custom widget. I don't like it and I can't find a way around. I marked that place in the source with ///!!! in main_form.cpp
Second is that my properties are loaded in the glade file but they are not set to the default value and when I change them from glade I can't get the new values. I marked the place where I try connecting a signal again with ///!!! in area.cpp

---

### Post by DrPepper836 on 2010-04-18
Is the visible property on your widget set to yes? Some versions of Glade set it to no for some reason, so you always had to change the default. When I was learning how to use Glade, it took me around 2 hours to figure that out.

---

### Post by mazzzterZ on 2010-04-19
> **DrPepper836 said:**
> Is the visible property on your widget set to yes? Some versions of Glade set it to no for some reason, so you always had to change the default. When I was learning how to use Glade, it took me around 2 hours to figure that out.

It is set to yes.

---

### Post by pbrane on 2010-04-19
Have you seen this?
[http://library.gnome.org/devel/gtkmm-tutorial/unstable/index.html]("http://library.gnome.org/devel/gtkmm-tutorial/unstable/index.html")

There is a section on custom containers and custom widgets. Looks like you are implementing a custom container.

---

### Post by mazzzterZ on 2010-04-19
> **pbrane said:**
> Have you seen this?
[http://library.gnome.org/devel/gtkmm-tutorial/unstable/index.html]("http://library.gnome.org/devel/gtkmm-tutorial/unstable/index.html")

There is a section on custom containers and custom widgets. Looks like you are implementing a custom container.

I don't know why I didn't tried it before, but your post gave me an idea. I removed all overloaded function and now it behaves as it should. It appears and all.
And not to make a new thread can somebody tell me how can I read the properties that I set in the glade file because when I get the widget with gtk::builder all of the properties are with their default value. Also I noticed that when I put my widget with glade in some container, it doesn't set the default properties but it shows that these properties have been changed( by making the name bold) and if I change them to their default value glade make the name not to be bold.

---

### Post by pbrane on 2010-04-19
What exactly do you mean "read the properties" in the glade file? You can look at the glade file in a text editor. It's XML. If you mean programmatically then you can call "get" functions to see what the values are. If you are editing a glade UI in the glade interface designer whatever values you set should be written to the glade file when you save it. I use glade3 and gtkmm for most of my projects. Glade has been saving the right values for me.

---

### Post by mazzzterZ on 2010-04-20
> **pbrane said:**
> What exactly do you mean "read the properties" in the glade file? You can look at the glade file in a text editor. It's XML. If you mean programmatically then you can call "get" functions to see what the values are. If you are editing a glade UI in the glade interface designer whatever values you set should be written to the glade file when you save it. I use glade3 and gtkmm for most of my projects. Glade has been saving the right values for me.

I mean to create my own properties that aren't part of the original widget itself. It looks like that if I just create Glib::Property variables
and then write it's arguments when I call my constructor:
[PHP]Area::Area(BaseObjectType* cobject, const Glib::RefPtr<Gtk::Builder>& refBuilder) : 
    //The GType name will actually be gtkmm__CustomObject__area 
    Glib::ObjectBase("Area"), 
    Gtk::Notebook(cobject), 
    integer(*this, "test1", 5), 
    dnumber(*this, "test3", 12.03), 
    boolean(*this, "test4", true), 
    string(*this, "test5", "This is string") [/PHP]
and then define them in my catalog file:
[PHP]<properties> 
                <property name="TEST1" id="test1" save="True" /> 
                <property name="TEST3" id="test3" save="True" /> 
                <property name="TEST4" id="test4" save="True" /> 
                <property name="TEST5" id="test5" save="True" /> 
            </properties> [/PHP]
when I start glade these 5 properties are there but they are all set to 0 and they show that they have been changed by making the name bold. For example when I put my widget in some container the property TEST1 is 0(and the name is bold) and if I change it to value 5 it recognize the default value and the name gets unbold. So let's say I change all of the properties in the glade file and save. If I look the XML file of *.ui it's alright with the correct values in it, but when I start my application the values of the properties are all the default that I set in the constructor but not the ones I set in my glade file. Also if I didn't set a default value for property it's 0 when my application starts(and again not the value that is set in the glade file).

---

