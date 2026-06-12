---
title: "gtkmm - disable radio button"
date: 2010-03-13
forum: Programming Talk
---

### Post by tbastian on 2010-03-13
I have a (hopefully) really simple question.

How do you disable radio buttons (ie gray them out) using gtkmm? I've searched the API and I can't find any obvious way of doing this...

Is it even possible?

---

### Post by SledgeHammer_999 on 2010-03-13
[Gtk::RadioButton](http://library.gnome.org/devel/gtkmm/unstable/classGtk_1_1RadioButton.html) derives from [Gtk::Widget](http://library.gnome.org/devel/gtkmm/unstable/classGtk_1_1Widget.html) (see class hierarchy on the top of the page).

All you have to do is call [Gtk::Widget::set_sensitive().](http://library.gnome.org/devel/gtkmm/unstable/classGtk_1_1Widget.html#a3192b5f7f4c15876169b913eb9d1075e) Eg:
[php]
.....
Gtk::RadioButton my_radio_button;
my_radio_button.set_sensitive(false);
....
[/php]

---

### Post by tbastian on 2010-03-15
thanks! I'll give that a try and let you know how it turns out.

---

### Post by tbastian on 2010-03-16
that worked out great, thanks again!

---

### Post by SledgeHammer_999 on 2010-03-16
no problem.

---

