---
title: "[Gtkmm] How to add blank space of fixed width"
date: 2010-02-16
forum: Programming Talk
---

### Post by kahumba on 2010-02-16
Hi,
I know it's possible in Gtk I saw such code but can't recall where or what it looks like. Probably there is a special widget.

Java folks do it this way:

```

jpanel.add(**Box.createHorizontalStrut**(int howMuchBlankSpace));

```

---

### Post by SledgeHammer_999 on 2010-02-16
I think you are refering to "padding". sample doc link->[http://library.gnome.org/devel/gtkmm/unstable/classGtk_1_1Box.html#a31aa59034a669239c4b99a9ced5742d6](http://library.gnome.org/devel/gtkmm/unstable/classGtk_1_1Box.html#a31aa59034a669239c4b99a9ced5742d6)

---

### Post by kahumba on 2010-02-16
Well unfortunately that one adds space on **both** sides of the widget.

---

### Post by SledgeHammer_999 on 2010-02-16
Maybe try using multiple containers like the pic shows(I know it's messy):

[[IMG]http://img24.imageshack.us/img24/1198/examplelayout.th.jpg[/IMG]](http://img24.imageshack.us/i/examplelayout.jpg/)

I think if you only put one child in a box container it will put the padding only on one side(depending if you used pack_start() or pack_end())

---

### Post by kahumba on 2010-02-16
Thanks, but I'd really wanna avoid such an approach. I (seem to) remember I saw a very simple Gtk solution to this and the code was very short. But it was months ago and can't figure out where I saw it. I got a book on Gtk+ & C, I'll give it a look through, maybe I saw it there.

---

### Post by SledgeHammer_999 on 2010-02-16
Hmm, one other relevant option is [Gtk::Box::set_spacing()](http://library.gnome.org/devel/gtkmm/unstable/classGtk_1_1Box.html#ab5396cb1385f8259bb49a0c78b55087b)

---

### Post by steeleyuk on 2010-02-16
You could use a GTK Alignment widget. That allows individual padding values for top, left, right, bottom.

---

### Post by kahumba on 2010-02-16
Thanks! Works fine. Problem solved, but if someone has a less verbose solution - I'd like to hear from him.

This is how I use your suggestion to create a 50px wide blank space:
```

Gtk::Alignment *al = Gtk::manage(new Gtk::Alignment());
al->set_size_request(50, 2);
hbox->pack_start(*al, false, true);

```

---

