---
title: "[Gtk] A different scroll approach possible?"
date: 2012-03-17
forum: Programming Talk
---

### Post by t1497f35 on 2012-03-17
Hi,
I'm using a Gtk::DrawingArea to manually draw a long vertical list.

It's inside a ScrolledWindow which only allows scrolling my vertical long list if I make the (vertical) size of the DrawingArea correspondingly large, but since I'm drawing stuff manually - it's a superfluous requirement which has a few bad side effects.

Can I get a **scrolling** widget with Gtk::ScrolledWindow **without** making it larger than the currently viewable area? Or do I have to implement my own Gtk::ScrolledWindow for that?

---

### Post by CynicRus on 2012-03-17
```

#include <gtkmm.h>

int main(int argc, char* argv[])
{
  Gtk::Main kit(argc, argv);
  Gtk::Window window;
  window.set_default_size( 400, 400 );

  Gtk::ScrolledWindow scrolledwindow;
  window.add(scrolledwindow);

  Gtk::DrawingArea drawingarea;
  drawingarea.set_size_request( 700, 700 );
  scrolledwindow.add(drawingarea);

  window.show_all_children();

  Gtk::Main::run(window);
  return 0;
}

``` if i understand the problem.

---

### Post by t1497f35 on 2012-03-17
Thanks,
here's an example:
Say I got 160 items (items=bunch of strings) each of each is 10 pixels tall, so normally I need to make the widget (the Gtk::DrawingArea) 1600 pixels high, otherwise the user can't scroll to the end of the list because the ScrolledWindow decides when the DrawingArea is scrollable based on its height (size).

But since I'm painting the items manually inside the Gtk::DrawingArea - I only paint the currently visible ones, only about 20 of them: 20 * 10 = 200pixels.

Example: if user scrolled to vertical position 400px then I compute the starting index in my array of items: 400/10 = 40 and draw the next 20 ones in a loop, thus I only draw items from my array in the range 40-60, not 0-160, hence I always need only the viewable area, I don't need more space - the ScrolledWindow does.

If you've ever drawn a long list manually inside a scrollable area you probably know what I mean.

So I'm basically asking - can the ScrolledWindow make a widget scrollable based not on its height, but on some other input which I could customize to my needs?

---

### Post by CynicRus on 2012-03-17
[http://inti.sourceforge.net/tutorial/libinti/cwscrolledwindows.html]("http://inti.sourceforge.net/tutorial/libinti/cwscrolledwindows.html") - maybe this can help you.

---

