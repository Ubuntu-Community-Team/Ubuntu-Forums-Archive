---
title: "gtkmm dynamically add tabs to notebook"
date: 2010-12-12
forum: Programming Talk
---

### Post by Woody1987 on 2010-12-12
I have a notebook widget with which I want to dynamically add new tabs to. So far I have:

```

Gtk::Label tabLabel;
Gtk::Notebook mainNotebook;
Gtk::HBox tabHbox;

for(int i = 0; i < numPortfolios(); i++)
{
    tabLabel.set_text(getPortfolio(i).getName());
    mainNotebook.append_page(tabHbox, tabLabel);
}

```

This compiles without any errors or warnings but when it runs, I get:
> 
Gtk-WARNING **: Can't set a parent on widget which has a parent
Gtk-WARNING **: Can't set a parent on widget which has a parent


And then, when I click on a tab I get:
> 
GLib-GObject-WARNING **: /build/buildd/glib2.0-2.26.1/gobject/gsignal.c:2392: instance `0x2240e20' has no handler with id `149'
Gtk-CRITICAL **: IA__gtk_widget_get_visible: assertion `GTK_IS_WIDGET (widget)' failed
Gtk-CRITICAL **: IA__gtk_widget_show: assertion `GTK_IS_WIDGET (widget)' failed
Gtk-CRITICAL **: IA__gtk_widget_get_mapped: assertion `GTK_IS_WIDGET (widget)' failed
Gtk-CRITICAL **: IA__gtk_widget_unrealize: assertion `GTK_IS_WIDGET (widget)' failed
Gtk-CRITICAL **: IA__gtk_widget_unrealize: assertion `GTK_IS_WIDGET (widget)' failed
Gtk-CRITICAL **: IA__gtk_widget_is_toplevel: assertion `GTK_IS_WIDGET (widget)' failed
Gtk-CRITICAL **: IA__gtk_widget_is_toplevel: assertion `GTK_IS_WIDGET (widget)' failed
Gtk-CRITICAL **: IA__gtk_widget_destroy: assertion `GTK_IS_WIDGET (widget)' failedGtk-CRITICAL **: IA__gtk_widget_destroy: assertion `GTK_IS_WIDGET (widget)' failed


Only the last tab has a label, the others are blank. Clicking on other tabs does nothing but show the above errors.

---

### Post by SledgeHammer_999 on 2010-12-12
This is just a guess. For each tab you need to create a different instance of Gtk::HBox+Gtk::Label. In your code you try to append the same instances to multiple tabs(containers). This only works for the first iteration of the "for loop". On the next iterations the widgets(tabHBox+tabLabel) already have a parent(the first tab) thats why Gtk refuses to add them in the subsequent tabs-parents.

This MAY solve your problem:
[php]
Gtk::Notebook mainNotebook;


for(int i = 0; i < numPortfolios(); i++)
{
    Gtk::Label tabLabel;
    Gtk::HBox tabHbox;


    tabLabel.set_text(getPortfolio(i).getName());
    mainNotebook.append_page(tabHbox, tabLabel);
}[/php]

The code above creates a new instance of Gtk::HBox+Gtk::Label in each iteration of the for loop.

---

### Post by Woody1987 on 2010-12-12
Thanks, but it doesnt work. No tabs are created at all using your code. 

I read somewhere that I could use Gtk::manage(). Is this right? If so, how?

---

### Post by Woody1987 on 2010-12-12
Solved it:

```

for(int i = 0; i < numPortfolios(); i++)
{
    Label *tabLabel = Gtk::manage(new Label(getPortfolio(i).getName()));
    HBox *tabHbox = Gtk::manage(new HBox());
    mainNotebook.append_page(*tabHbox, *tabLabel);
}

```

---

### Post by Woody1987 on 2010-12-12
I now have another problem relating to this. After the page is appended, I want to pass the HBox to a function to pack widgets into it.

```

void createTabs()
{
    for(int i = 0; i < numPortfolios(); i++)
    {
        Label *tabLabel = manage(new Label(getPortfolio(i).getName()));
        HBox *tabHbox = manage(new HBox());
        mainNotebook.append_page(*tabHbox, *tabLabel);
        createTabContent(getPortfolio(i), tabHbox);
    }
}

void createTabContent(Portfolio p, HBox *hbox)
{
    Button a("test");
    hbox->pack_start(a);
}

```

The above compiles fine, but the button I created does not show.

---

### Post by Woody1987 on 2010-12-12
Solved it again.

```

void createTabContent(Portfolio p, Gtk::HBox *hbox)
{
    Button *a = manage(new Button("test"));
    hbox->pack_start(*a);
}

```

---

