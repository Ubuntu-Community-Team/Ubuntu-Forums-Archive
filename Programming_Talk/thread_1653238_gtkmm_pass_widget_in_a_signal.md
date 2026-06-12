---
title: "gtkmm pass widget in a signal"
date: 2010-12-26
forum: Programming Talk
---

### Post by Woody1987 on 2010-12-26
I have an event box which when clicked needs a HBox passed to the receiving function.

```

HBox *hbox = manage(new HBox);
EventBox *titleEvent = manage(new EventBox);
titleEvent->signal_button_press_event().connect(sigc::bind<HBox>(sigc::mem_fun(*this, &MainWindow::showHome), *hbox));

bool MainWindow::showHome(GdkEventButton* event, HBox *hbox)
{
    return true;
}

```

I get these errors:
```

 initializing argument 2 of &#8216;sigc::bind_functor<-0x00000000000000001, T_functor, T_type1, sigc::nil, sigc::nil, sigc::nil, sigc::nil, sigc::nil, sigc::nil> sigc::bind(const T_functor&, T_type1) [with T_type1 = Gtk::HBox, T_functor = sigc::bound_mem_functor2<bool, MainWindow, GdkEventButton*, Gtk::HBox>]&#8217;
&#8216;Gtk::HBox::HBox(const Gtk::HBox&)&#8217; is private

```

If I pass for example a string instead, then it works fine. Is it possible to pass widgets this way?

---

### Post by worksofcraft on 2010-12-26
> **Woody1987 said:**
> I have an event box which when clicked needs a HBox passed to the receiving function.

```

HBox *hbox = manage(new HBox);
EventBox *titleEvent = manage(new EventBox);
titleEvent->signal_button_press_event().connect(sigc::bind<HBox>(sigc::mem_fun(*this, &MainWindow::showHome), *hbox));

bool MainWindow::showHome(GdkEventButton* event, HBox *hbox)
{
    return true;
}

```

I get these errors:
```

 initializing argument 2 of &#8216;sigc::bind_functor<-0x00000000000000001, T_functor, T_type1, sigc::nil, sigc::nil, sigc::nil, sigc::nil, sigc::nil, sigc::nil> sigc::bind(const T_functor&, T_type1) [with T_type1 = Gtk::HBox, T_functor = sigc::bound_mem_functor2<bool, MainWindow, GdkEventButton*, Gtk::HBox>]&#8217;
&#8216;Gtk::HBox::HBox(const Gtk::HBox&)&#8217; is private

```

If I pass for example a string instead, then it works fine. Is it possible to pass widgets this way?

Yes you can pass widgets to Gtk Signal handlers, however the error message you are getting indicates that it is trying to copy construct your Hbox.

Edit
Nope soz my analysis of the bug was wrong...

The bug is here instead:
```

titleEvent->signal_button_press_event().connect(sigc::bind<HBox>(sigc::mem_fun(*this, &MainWindow::showHome), *hbox));

```

You see *hbox IS creating a copy of what hbox points to.

You need to take the * off so that you pass the pointer...

p.s. or alternatively you can change showhome to take a reference as it's parameter.

---

### Post by dwhitney67 on 2010-12-27
I personally would have made the HBox a member of the class (i.e. MainWindow), thus obviating the need to pass it to the callback routine.

But some people like to do things the hard way, and that's cool.

---

### Post by Woody1987 on 2010-12-27
Thanks but it didnt work. But I have got it working by putting the hbox into a struct and passing that instead.

---

