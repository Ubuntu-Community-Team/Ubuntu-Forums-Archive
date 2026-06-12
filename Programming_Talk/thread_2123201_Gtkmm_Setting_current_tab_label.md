---
title: "Gtkmm: Setting current tab label?"
date: 2013-03-07
forum: Programming Talk
---

### Post by fallenshadow on 2013-03-07
I don't know why this seems so difficult but all I want to do is set the current tab label/title. Here is what I have so far:

```

        Gtk::Widget& widget = m_Notebook.get_current_page();
        Glib::ustring label = "TEST";
        m_Notebook.set_tab_label(widget, label);

```

The errors shown don't make much sense to me. :/

> 
mainwindow.cc:545:59: error: invalid initialization of non-const reference of type ‘Gtk::Widget&’ from an rvalue of type ‘int’
mainwindow.cc:547:47: error: no matching function for call to ‘Gtk::Notebook::set_tab_label(Gtk::Widget&, Glib::ustring&)’
mainwindow.cc:547:47: note: candidate is:
/usr/include/gtkmm-3.0/gtkmm/notebook.h:435:8: note: void Gtk::Notebook::set_tab_label(Gtk::Widget&, Gtk::Widget&)
/usr/include/gtkmm-3.0/gtkmm/notebook.h:435:8: note:   no known conversion for argument 2 from ‘Glib::ustring’ to ‘Gtk::Widget&’


Any help appreciated!

---

### Post by r-senior on 2013-03-07
The get_current_page() method returns the index number of the tab, not a widget:

[https://developer.gnome.org/gtkmm/3.0/classGtk_1_1Notebook.html#af45cfad58e0d5ed998c551ede9015dff](https://developer.gnome.org/gtkmm/3.0/classGtk_1_1Notebook.html#af45cfad58e0d5ed998c551ede9015dff)

To get the child widget, you need to pass the index number to get_nth_page(int page_num):

[https://developer.gnome.org/gtkmm/3.0/classGtk_1_1Notebook.html#aee6987ef10d8e3afcc40824c53f4c1ad](https://developer.gnome.org/gtkmm/3.0/classGtk_1_1Notebook.html#aee6987ef10d8e3afcc40824c53f4c1ad)

---

### Post by fallenshadow on 2013-03-07
This is what I have now:

```

        Gtk::Widget& widget = m_Notebook.get_nth_page(
                       m_Notebook.get_current_page());
        Glib::ustring label = "TEST";
        m_Notebook.set_tab_label(widget, label);

```

> 
mainwindow.cc:546:53: error: invalid initialization of non-const reference of type ‘Gtk::Widget&’ from an rvalue of type ‘Gtk::Widget*’
mainwindow.cc:548:47: error: no matching function for call to ‘Gtk::Notebook::set_tab_label(Gtk::Widget&, Glib::ustring&)’
mainwindow.cc:548:47: note: candidate is:
/usr/include/gtkmm-3.0/gtkmm/notebook.h:435:8: note: void Gtk::Notebook::set_tab_label(Gtk::Widget&, Gtk::Widget&)
/usr/include/gtkmm-3.0/gtkmm/notebook.h:435:8: note:   no known conversion for argument 2 from ‘Glib::ustring’ to ‘Gtk::Widget&’


Is this getting any closer? :confused:

---

### Post by spjackson on 2013-03-07
1. Dereference the pointer returned by get_nth_page.
2. Use set_tab_label**_text**.
```

        Gtk::Widget& widget = * m_Notebook.get_nth_page(
                       m_Notebook.get_current_page());
        Glib::ustring label = "TEST";
        m_Notebook.set_tab_label_text(widget, label);

```

---

### Post by fallenshadow on 2013-03-07
Thanks! :) (how do I mark this as solved? - not used to the new forum)

---

### Post by fallenshadow on 2013-03-07
Oh dear, it seems doing this will get rid of the close button for that tab. What would be the right solution for this?

Re-add a close button?

---

### Post by r-senior on 2013-03-07
I think the trick is that the tab label is a GtkWidget, as opposed to a GtkLabel. The gtk_notebook_set_tab_label_text() function is a convenience function that creates a GtkLabel and sets it as the widget for the tab's label. If you want to have a label and icon as the tab label, you need a container widget, e.g. a GtkBox that contains a GtkLabel and GtkImage/GtkButton. Then you use gtk_notebook_set_tab_label() instead of gtk_notebook_set_tab_label_text(). Expose the label as a property and connect up a signal to the image/button. 

Sorry for quoting the C functions -- you know what I mean.

There's an example here, not in C++ but GTK is GTK:

[http://stackoverflow.com/questions/2581902/creating-a-closeable-tab-in-mono-gtk](http://stackoverflow.com/questions/2581902/creating-a-closeable-tab-in-mono-gtk)

---

### Post by pbrane on 2013-03-07
The actual tab widget has changed with your code. Remember you are using a custom function to create a notebook page tab with a close button. If you look at the add_page function in mainwindow.cc you'll see how the initial label is added. 

```

Gtk::Label *label = Gtk::manage(new Gtk::Label(text));

```

you need to get a pointer/reference to that label widget to change the text. Something like this may work:
```

Gtk::Widget& widget = *m_Notebook.get_nth_page(m_Notebook.get_current_page());
Gtk::Widget label = widget.get_tab_label(widget);
label.set_text(Glib::ustring("TEST"));

```

I'm not sure if this is the correct code but it is the general idea.

---

### Post by fallenshadow on 2013-03-08
Thanks for the ideas! Yes pbrane this is what I really need to do, change the text of the label without disturbing the close button.

The widget class seems to have alot of functions: [https://developer.gnome.org/gtkmm/3.5/classGtk_1_1Widget.html]("https://developer.gnome.org/gtkmm/3.5/classGtk_1_1Widget.html")

However, I can't see ones that would be of any use. As far as I understand widget is a class for general usage with any gtk widget, right? So it may not contain specific functions like what you mentioned.

> mainwindow.cc:551:31: error: &#8216;class Gtk::Widget&#8217; has no member named &#8216;get_tab_label&#8217;
mainwindow.cc:552:9: error: &#8216;class Gtk::Widget&#8217; has no member named &#8216;set_text&#8217;

Im not so sure its possible to use widget functions to get what I need but you are definitely on the right track idea wise.

---

### Post by fallenshadow on 2013-03-10
Bump :S

---

### Post by fallenshadow on 2013-04-08
I came back to this today, I know im pretty close now. Just stuck on this final piece of the puzzle:

> &#8216;class Gtk::Widget&#8217; has no member named &#8216;set_text&#8217;

Of course this is due to trying set_text a Label method on a widget. Can a widget be converted to GTK:Label so I can use set_text?

```
label.set_text(Glib::ustring("TEST"));
```

---

### Post by r-senior on 2013-04-08
A label is a widget (subclass of) so you can cast it as long as it really is a label, ie it was created as a new label but declared as a widget variable. This is very common in C programming with Gtk but I don't know specifically how to do it in C++. I suspect it's just a simple cast.

---

### Post by fallenshadow on 2013-04-08
When you say simple cast do you mean a static cast?

---

### Post by r-senior on 2013-04-10
I probably meant a static cast but I've had a play around with it and I don't think you need one:

This is really crude, but I think it's the basic idea, i.e. create a widget (in this case a Hbox subclass) that combines the label and close button., then add that as the tab label.

*notebook.cc*
```
#include <gtkmm.h>
#include "closelabel.h"

int main(int argc, char *argv[])
{
    Gtk::Main kit(argc, argv);
    Gtk::Window window;
    window.set_title("Notebook");
    window.set_default_size(600, 400);

    Gtk::VBox vbox;
    window.add(vbox);

    Gtk::Notebook notebook;

    Gtk::Label label0("Content Alpha");
    CloseLabel tabLabel0("Alpha");
    notebook.append_page(label0, tabLabel0);

    Gtk::Label label1("Content Beta");
    CloseLabel tabLabel1("Beta");
    notebook.append_page(label1, tabLabel1);

    vbox.pack_start(notebook);
    window.show_all();
    Gtk::Main::run(window);
}
```

*closelabel.h*
```
#ifndef CLOSELABEL_H
#define CLOSELABEL_H

#include <gtkmm.h>

class CloseLabel : public Gtk::HBox
{
public:
    CloseLabel(const char *text);

protected:
    void on_close_button_clicked();
    Gtk::Label tab_label;
    Gtk::Button close_button;
};

#endif

```

*closelabel.cc*
```
#include "closelabel.h"
#include <iostream>

CloseLabel::CloseLabel(const char *text)
    : tab_label(text), close_button("close")
{
    close_button.signal_clicked().connect(
        sigc::mem_fun(*this, &CloseLabel::on_close_button_clicked)
    );
    pack_start(tab_label);
    pack_start(close_button);
    show_all();
}

void CloseLabel::on_close_button_clicked()
{
    std::cout << "on_close_button_clicked" << std::endl;
}

```

It needs some work. You'd need to keep track of the notebook page in the CloseLabel class so that you know which one to close in the handler. And, obviously, you'd use a nice little little "X" icon as an image rather than the ugly close button.

As you know, my C++ is not brilliant, but I think this is the way forward with these closeable tabs in GTK3.

---

