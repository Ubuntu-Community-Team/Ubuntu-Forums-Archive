---
title: "[C++]Interaction between Gtkmm and Pango"
date: 2011-11-23
forum: Programming Talk
---

### Post by ehmicky on 2011-11-23
Hi everyone,

I've got some issues while trying to use Pangomm inside Gtkmm. The methods get_layout() from Gtk::Entry and Gtk::Label provides a Pango::Layout, but when this Pango::Layout is changed, the Gtk::Entry or Label is not updated. How to do so ?
For example :
```
#include    <gtkmm.h>

class MyWindow : public Gtk::Window
{
    protected:
        Gtk::Label label;
        Pango::AttrList attrlist;
        Pango::AttrInt attribut;
    public:
        MyWindow( void ) 
            : label( "This is a label" ),
                attribut( Pango::Attribute::create_attr_underline( Pango::UNDERLINE_DOUBLE ) )
        {
            add( label );
            attrlist.change( attribut );
            label.get_layout()->set_attributes( attrlist );
            show_all_children();
        }
};

int main(int argc, char* argv[])
{
    Gtk::Main kit( argc, argv );
    MyWindow window;
    Gtk::Main::run( window );
    return 0;    
}
```
Compiled with :
```
$ g++ $(pkg-config gtkmm-3.0 --cflags --libs) && ./a.out
```
Doesn't show a label with double underlines.

Thank you very much !

---

### Post by ehmicky on 2011-11-25
A little up.
Sorry for it, but I've learned all Pango, and I feel like I can't use it for my primary goal (manipulating GTK+ text), it's a bit frustratring :(

---

### Post by crdlb on 2011-11-25
At least for GtkLabel, you can use the set_attributes method on the widget itself. If you can't do something similar for GtkEntry, you could use GtkTextView, which can be modified with GtkTextTag objects.

---

### Post by ehmicky on 2011-11-25
Thanks for your reply,
Indeed Gtk provides most of the things for Gtk::Entry and Gtk::Label that can be achieved though a Pango::layout. However, there are still few interesting things missing, such as setting a set of fonts with fallback fonts, which can be interesting for internationalization.
get_layout()  returns a Glib::RefPtr, so I think the intention of the library is to let us modify the Pango::Layout by reference, but curiously, the changes made are not updated.

---

