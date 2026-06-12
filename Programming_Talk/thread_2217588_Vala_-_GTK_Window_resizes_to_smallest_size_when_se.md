---
title: "Vala - GTK Window resizes to smallest size when setting resizable"
date: 2014-04-18
forum: Programming Talk
---

### Post by slooksterpsv on 2014-04-18
Vala!

I'm porting my app from Qt over to Vala for use with GTK systems in case others don't want QT libraries on their system, but I'm running into an issue:

The issue is when I set this.resizable or window.resizeable or even using window.set_resizable () the window sizes itself down to the smallest size, instead of keeping the size I set it at.

I don't want the user to be able to control the window size and I want specific dimensions. I've tried using set_default_geometry as well as set_default_size to even this(or window).height = this.width = 

It always resizes.

Extra info: I don't have any content in the window, as I don't think it should matter, it may but I hope not.

Any one have any idea how to resolve this?

Here's the base code I'm working with:

```

using Gtk;

public class EFIBootOrder : Window {
	public EFIBootOrder () {
		this.title = "EFI Boot Order GTK";
		this.border_width = 10;
		this.window_position = WindowPosition.CENTER;
		this.default_height = 390;
		this.default_width = 275;
		
	}
}

int main (string[] args) {
	Gtk.init (ref args);

	var window = new EFIBootOrder ();

	window.destroy.connect (Gtk.main_quit);
	window.show_all ();
	

	Gtk.main ();
	return 0;
}

```

---

