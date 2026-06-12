---
title: "[Gtkmm] Combo box"
date: 2012-12-09
forum: Programming Talk
---

### Post by bird1500 on 2012-12-09
Hi,
It seems to me gtk/mm doesn't provide an easy way to add an item, you have to create a mini model/view shebang.
After googling seems to me the Python backend does have an append_text() method.

So, is there a simple way to add items to the Gtk::ComboBox (in C or C++)?

---

### Post by SuperCamel on 2012-12-09
As far as I know, there is no simpler way. You do need to create a model, like in the Gtkmm examples. I'd love to be proven wrong though!

---

### Post by SledgeHammer_999 on 2012-12-09
First of all, the model-view paradigm is used by Qt too and I think it is very useful. Anyway for simply adding new text items you could use [Gtk::ComboBoxText](http://developer.gnome.org/gtkmm/unstable/classGtk_1_1ComboBoxText.html)

---

### Post by bird1500 on 2012-12-09
Thanks, that's what I've been looking for, though creating a new class, rather than just adding the simple methods to the combo box, is a bad idea imo, though typical of gtk.

---

### Post by SledgeHammer_999 on 2012-12-09
Well it is a good design approach. Imagine if you did the necessary actions with a regular Combobox. Sooner or later you would end up subclassing Combobox and wrapping your methods inside this subclass.

Regular Combobox is useful, for when you want to do advanced things, like display images/text/checkboxes (or all of these) in each item entry.

---

### Post by bird1500 on 2012-12-10
Adding a method (or a few of them) to simplify things and having a powerful widget don't exclude each other, example: I've used Java's swing - it has both in one class, very handy.

Another example of them (over)using the silly subclassing solution is H/VButtonBox, H/VBox, etc, one doesn't need to be a genius to realize this is silly, apparently they finally realized this and declared those classes deprecated and recommend using the parent ones instead (ButtonBox, Box, etc).

They have other silly thingies, like instead of using a single method like setVisible(true/false), they created 2 different methods (hide, set_visible), or using in a single var name both camel case and underlines in their tutorial - gosh, one can't find a sillier naming approach of variables.

---

