---
title: "How do i add scroll bars in Gtk::Window in Gtkmm"
date: 2014-04-13
forum: Programming Talk
---

### Post by tejashs on 2014-04-13
Hi I have a derived Gtk::Window (c++) object in my application and am not sure how too begin adding scroll bars to it.
Have anyone else done it before?? if so can you give me an example

---

### Post by slickymaster on 2014-04-14
Have you already read the respective class reference: [gtkmm: Gtk::ScrolledWindow ]("https://developer.gnome.org/gtkmm/unstable/classGtk_1_1ScrolledWindow.html")

---

### Post by tejashs on 2014-04-14
Yes i have looked at Scrolled window before but i am running into some trouble using that and it is not behaving as i want it to.

---

### Post by tejashs on 2014-04-14
So i have been digging around more, but i have 1 more question, 
if i use Gtk::Scrollbar do i need to handle what is shown next myself, is that the idea behind scrollbar, find the position of the scrollbar(s) and calculate and show whats to be shown??

---

### Post by ofnuts on 2014-04-15
Yes, but this is what the ScrolledWindow is going to do for you (on two axes). What is the ScrolledWindow not doing as you want?

---

### Post by tejashs on 2014-04-15
1) ```
ScrolledWindow::override_background_color() 
``` dosent seem to work 
2) I am listening to key pressed event in Gtk::Window and so the scroll bar dosent resond to the keys pressed (Arrows, home, end, page up, page down)

```

class mycalss : public Gtk::Window
{

private:
Gtk::ScrolledWindow mSW;
Gtk::Alignment mAl;
//Others
};

myclass()
{
mSW.add(mAl);
add(mSW);
override_background_color(Gdk::RGBA( BLACK )); // over ride for window or all it sdosent work, if i just remove the scrolled window it works
mSW.override_background_color(Gdk::RGBA( BLACK ));
mAl.override_background_color(Gdk::RGBA( BLACK ));

add_events( Gdk::KEY_PRESS_MASK | Gdk::STRUCTURE_MASK );
}

bool myclass::on_key_press_event( GdkEventKey *eventkey )
{
       // Handle keypress: but since i am handling here how does it propogate to scrolled window??
}


```

---

### Post by ofnuts on 2014-04-15
1) "doesn't work" != "don't know how to make it work".

2) See [this](https://developer.gnome.org/gtkmm-tutorial/stable/sec-keyboardevents-propagation.html.en).

---

### Post by tejashs on 2014-04-18
1)  so normally it should work, when i dont use scrolled window and add the Gtk:;Alignment directly into window, the background changes,  but when i introduce the scrolled window in the middle, background dosent change.

2.1)So from the documentation I have called Gtk::Window::on_key_press_event() inside my virtual function, but scrolled window dosent seem to respond to arow keys, but it is scrolls to page up,page down, home , end.

2.2) Is it possible to scroll when I drag the screen??

---

