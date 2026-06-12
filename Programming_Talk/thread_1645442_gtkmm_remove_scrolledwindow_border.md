---
title: "gtkmm remove scrolledwindow border"
date: 2010-12-14
forum: Programming Talk
---

### Post by Woody1987 on 2010-12-14
I want to remove the scrolledwindow frame. I want this done in gtkmm. Thanks.

---

### Post by SledgeHammer_999 on 2010-12-14
What do you mean by "scrolledwindow frame"? Can you provide a screenshot showing the "frame"?

---

### Post by Woody1987 on 2010-12-15
Image shows a grey border around the contents of the scrolledwindow. I would like this removed.

---

### Post by SledgeHammer_999 on 2010-12-15
I am not really sure if this will work. Gtk::ScrolledWindow is derived from Gtk::Container. Try setting the border width to 0. [Gtk::Container::set_border_width()](http://library.gnome.org/devel/gtkmm/unstable/classGtk_1_1Container.html#a18b32244cb55a8eb34f9c6f195c8e5bc)

---

### Post by dwhitney67 on 2010-12-15
I would suggest looking into the ScrolledWindow's set_shadow_type().  Consider setting it to Gtk::SHADOW_NONE.

---

### Post by Woody1987 on 2010-12-15
Thanks for your suggestions but neither set_border_width() or set_shadow_type() worked.

---

### Post by dwhitney67 on 2010-12-15
Besides the Gtk::Window, is your Gtk::ScrolledWindow encapsulated within another container?

Also, did you design your GUI using Glade, or did you do it the "traditional" way?  If the latter, could you post a little more code (if not all of it), so that the anomaly can be reproduced by others.  Your posted image is very small, and does not offer sufficient information.

---

### Post by Woody1987 on 2010-12-15
Ok, i figured out its not the scrolledwindow. If I dont put anything inside it, there is no frame. But, if I add a VBox for example to it then the frame appears. 

The ScrolledWindow is contained within a VBox.

```

VBox *left = manage(new VBox);

ScrolledWindow *stockScroll = manage(new ScrolledWindow);
stockScroll->set_policy(POLICY_NEVER, POLICY_AUTOMATIC);
stockScroll->set_shadow_type(SHADOW_NONE);

VBox *stockScrollVbox = manage(new VBox);
stockScrollVbox->set_spacing(15);

left->pack_start(*stockScroll, TRUE, TRUE, 0);
stockScroll->add(*stockScrollVbox);

```

---

### Post by SledgeHammer_999 on 2010-12-15
Maybe:
[php]stockScrollVbox->set_border_width(0);[/php]

---

### Post by Woody1987 on 2010-12-15
> **SledgeHammer_999 said:**
> Maybe:
[php]stockScrollVbox->set_border_width(0);[/php]

Didn't work.

---

### Post by nvteighen on 2010-12-15
> **Woody1987 said:**
> 
```

VBox *left = manage(new VBox);

ScrolledWindow *stockScroll = manage(new ScrolledWindow);
stockScroll->set_policy(POLICY_NEVER, POLICY_AUTOMATIC);
stockScroll->set_shadow_type(SHADOW_NONE);

VBox *stockScrollVbox = manage(new VBox);
stockScrollVbox->set_spacing(15);

left->pack_start(*stockScroll, TRUE, TRUE, 0);
stockScroll->add(*stockScrollVbox);

```

In GTK+, scrollbars are disabled by default. The way they're used in this snippet isn't exactly how I would do it, but if all you want is to eliminate the scroll, use this:

```

VBox *left = manage(new VBox);
left->pack_start(theObjectToPack, TRUE, TRUE, 0);

```

theObjectToPack should be the object to be packed first.

---

### Post by Woody1987 on 2010-12-15
> **nvteighen said:**
> In GTK+, scrollbars are disabled by default. The way they're used in this snippet isn't exactly how I would do it, but if all you want is to eliminate the scroll, use this:

```

VBox *left = manage(new VBox);
left->pack_start(theObjectToPack, TRUE, TRUE, 0);

```

theObjectToPack should be the object to be packed first.

The scrollbar isnt the problem, its the frame that it draws around its contents.

---

### Post by Regunirun on 2011-03-29
> **Woody1987 said:**
> The scrollbar isnt the problem, its the frame that it draws around its contents.

Was this ever resolved? I'm having the same issue :/

---

### Post by danielrichter on 2011-04-27
I had this issue too. But then I found this wonderful solution: [http://www.mail-archive.com/gtkmm-list@gnome.org/msg03509.html](http://www.mail-archive.com/gtkmm-list@gnome.org/msg03509.html)

---

