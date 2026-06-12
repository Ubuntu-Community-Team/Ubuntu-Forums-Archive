---
title: "automatically resize a window"
date: 2010-06-25
forum: Programming Talk
---

### Post by tbastian on 2010-06-25
I'd like to be able to add a widget to a window, have the window expand, remove the widget and have the window automatically resize to its original size. I put together an example if it helps.

```

#include <gtkmm.h>

Gtk::HBox * hbox;
Gtk::Button * button1;
Gtk::Button * button2;
Gtk::Window * window;
int packed;

void other_button_clicked ()
{
	if ( packed ) {
		hbox -> remove ( *button2 );
		packed = 0;
	}
}

void on_button_clicked ()
{
	if ( ! packed ) {
		hbox -> pack_start ( *button2, Gtk::PACK_SHRINK );
		button2 -> show ();
		packed = 1;
	}
}

int main ( int argc, char ** argv )
{
	Gtk::Main kit ( argc, argv );

	window = new Gtk::Window ();
	hbox = Gtk::manage ( new Gtk::HBox ());

	button1 = Gtk::manage ( new Gtk::Button ( "button 1"));
	button2 = Gtk::manage ( new Gtk::Button ( "button 2"));

	button1 -> signal_clicked () . connect (
		sigc::ptr_fun ( &on_button_clicked ));

	button2 -> signal_clicked () . connect (
		sigc::ptr_fun ( &other_button_clicked ));

	hbox -> pack_start ( *button1, Gtk::PACK_SHRINK );

	window -> add ( *hbox );

	window -> show_all_children ();

	packed = 0;

	Gtk::Main::run ( *window );

	delete window;
	return 0;
}

```

one can compile it using this line:
```
g++ -o widget_adding widget_adding.cc `pkg-config gtkmm-2.4 --cflags --libs`

```

---

### Post by tbastian on 2010-06-28
bump...

---

### Post by PaulM1985 on 2010-06-28
I would have thought that you could store the original size of the window before it expands and then once the widget is removed you can set the window back to its original size.

Paul

---

### Post by tbastian on 2010-06-28
That turns out to work! thanks Paul... the first time I tried it I had switched the 'height' and 'width' arguments to the resize call, which made me think that it wouldn't work very well.

[php]
#include <gtkmm.h>

Gtk::HBox * hbox;
Gtk::Button * button1;
Gtk::Button * button2;
Gtk::Window * window;
int packed;
int height, width;

void other_button_clicked ()
{
	if ( packed ) {
		hbox -> remove ( *button2 );
		window -> resize ( width, height );
		packed = 0;
	}
}

void on_button_clicked ()
{
	if ( ! packed ) {
		height = window -> get_height ();
		width = window -> get_width ();
		hbox -> pack_start ( *button2, Gtk::PACK_SHRINK );
		button2 -> show ();
		packed = 1;
	}
}

int main ( int argc, char ** argv )
{
	Gtk::Main kit ( argc, argv );

	window = new Gtk::Window ();
	hbox = Gtk::manage ( new Gtk::HBox ());

	button1 = Gtk::manage ( new Gtk::Button ( "button 1"));
	button2 = Gtk::manage ( new Gtk::Button ( "button 2"));

	button1 -> signal_clicked () . connect (
		sigc::ptr_fun ( &on_button_clicked ));

	button2 -> signal_clicked () . connect (
		sigc::ptr_fun ( &other_button_clicked ));

	hbox -> pack_start ( *button1, Gtk::PACK_SHRINK );

	window -> add ( *hbox );

	window -> show_all_children ();

	packed = 0;

	Gtk::Main::run ( *window );

	delete window;
	return 0;
}[/php]

---

### Post by PaulM1985 on 2010-06-28
I noticed on your last post that you have pointers to a window, 2 buttons and a HBox, but you only delete the window at the end of the program.  You should probably look to delete the other three components aswell because I am not sure if deleting the window would also delete them.

Paul

---

### Post by tbastian on 2010-06-28
Since I use Gtk::manage, Gtk automatically deals with the pointers once the parent is destroyed.

---

