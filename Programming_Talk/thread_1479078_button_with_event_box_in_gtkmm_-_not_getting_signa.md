---
title: "button with event box in gtkmm - not getting signals"
date: 2010-05-10
forum: Programming Talk
---

### Post by tbastian on 2010-05-10
Hello all,

I'm trying to create a button in gtkmm using a label inside an event box. In the constructor I enable button_press events, and assign my own callback function for everytime the button is pressed. That works just fine.

When I try to use the button in another application, I try to add another callback so that I can do other stuff whenever the button is pressed. This DOESN'T work.

Could anybody tell me why??

```
bool on_button_press ( GdkEventButton * event, Glib::ustring string )
{
	std::cout << string << "\n";
	return true;
}

int main ( int argc, char ** argv )
{
	Gtk::Main kit ( argc, argv );

	MyButton * button = new MyButton ( "this is a button" );
	Gtk::Window * window = new Gtk::Window ();

	button -> signal_button_press_event () . connect ( 
			sigc::bind <Glib::ustring> ( sigc::ptr_fun ( &on_button_press ),
									"string" ), true );

	window -> set_title ( "test button" );
	window -> set_default_size ( 100, 100 );

	window -> add ( *button );

	window -> show_all_children ();

	Gtk::Main::run ((Gtk::Window&) *window );

	return 0;
}
```

```
class MyButton : public Gtk::EventBox
{
	private:
		Glib::ustring name;
		Gtk::Label label;
		bool active;
		Gdk::Color color;

		virtual bool on_clicked_event ( GdkEventButton * event, MyButton * button );
		
	public:
		MyButton ( Glib::ustring name );
		virtual ~MyButton ();
		void set_active ( bool active );
		bool get_active ();
};
```

```
MyButton::MyButton ( Glib::ustring name )
	: name ( name ),
	  label ( name )
{
	active = false;
	this -> add ( label );
	this -> set_events ( Gdk::BUTTON_PRESS_MASK );
	this -> signal_button_press_event () . connect ( 
			sigc::bind <MyButton*> ( sigc::mem_fun ( *this, &MyButton::on_clicked_event ),
									this ), true );

	color . set ( "gray" );
	modify_bg ( Gtk::STATE_SELECTED, color );
}

MyButton::~MyButton () {}

bool MyButton::on_clicked_event ( GdkEventButton * event, MyButton * button )
{
	active = active ? false : true;

	if ( active ) {
		set_state ( Gtk::STATE_SELECTED );
	} else {
		set_state ( Gtk::STATE_NORMAL );
	}

	return true;
}

void MyButton::set_active ( bool active )
{
	this -> active = active ? false : true;

	if ( active ) {
		set_state ( Gtk::STATE_SELECTED );
	} else {
		set_state ( Gtk::STATE_NORMAL );
	}
}

bool MyButton::get_active ()
{
	return active;
}
```

---

### Post by tbastian on 2010-05-11
As it turns out, apparently you can't connect the same signal twice to the same object. It seems to only respect the first signal.

---

### Post by SledgeHammer_999 on 2010-05-11
Is there any special purpose you want to have this kind of button?
If not, then you can use a Gtk::Button and use Gtk::Button::set_relief(Gtk::RELIEF_NONE). This will make it appear as if it is a "clickable-label" visually.

---

### Post by SledgeHammer_999 on 2010-05-11
> **tbastian said:**
> As it turns out, apparently you can't connect the same signal twice to the same object. It seems to only respect the first signal.

No you can. Just return false in your MyButton::on_clicked_event this propagates the signal further. Link-->[http://library.gnome.org/devel/gtk/stable/GtkWidget.html#GtkWidget-button-press-event](http://library.gnome.org/devel/gtk/stable/GtkWidget.html#GtkWidget-button-press-event)

---

### Post by tbastian on 2010-05-11
> **SledgeHammer_999 said:**
> No you can. Just return false in your MyButton::on_clicked_event this propagates the signal further. Link-->[http://library.gnome.org/devel/gtk/stable/GtkWidget.html#GtkWidget-button-press-event](http://library.gnome.org/devel/gtk/stable/GtkWidget.html#GtkWidget-button-press-event)

Thats it! Thanks a lot

---

### Post by tbastian on 2010-05-11
> **SledgeHammer_999 said:**
> Is there any special purpose you want to have this kind of button?
If not, then you can use a Gtk::Button and use Gtk::Button::set_relief(Gtk::RELIEF_NONE). This will make it appear as if it is a "clickable-label" visually.

The main reason I'm doing this instead of just a toggle button, is because I'm constantly calling 'set active' and for a toggle button that also triggers the event which I really don't want.

---

