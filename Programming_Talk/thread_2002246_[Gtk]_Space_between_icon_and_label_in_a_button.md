---
title: "[Gtk] Space between icon and label in a button"
date: 2012-06-12
forum: Programming Talk
---

### Post by t1497f35 on 2012-06-12
Hi,
As one can see on the screenshot, there's too little space between the button's icon and its label. I haven't find a way to customize it. Does anyone know how?

Here's how I create the buttons:
[PHP]
//to make sure the icons show up
Gtk::Settings::get_default()->property_gtk_button_images() = true;

//method creating buttons
Gtk::Button*
Win::createButton(const Gtk::StockID &id) {
    Gtk::Button *p = Gtk::manage(new Gtk::Button(id));
    p->set_size_request(100, -1);
    return p;
}

//example:
pClipboardBtn = createButton(Gtk::Stock::COPY);
[/PHP]

---

### Post by r-senior on 2012-06-12
Hmm. I'd never noticed that but now it will annoy me!

Looks like a flaw in standard GTK3. It's not customizable -- those are stock buttons. Here's a dialog box from Gedit for example:

---

### Post by t1497f35 on 2012-06-12
Gee I still hope it's somehow customizable.. maybe we just don't know how.

---

### Post by t1497f35 on 2012-06-12
Here's another weirdness: if you set your own label (e.g. button.set_label("my label")) then the icon doesn't show up at all.

---

### Post by hakermania on 2012-06-12
How about, instead of "Save" you give it "     Save" (with 2-3 spaces before the 1st letter)?

---

### Post by pbrane on 2012-06-12
Create an empty button, add an hbox and then add the icon widget with spacing and then add the label widget with spacing.


[PHP]
Gtk::Button* create_button()
{
  Gtk::Button *button = Gtk::manage(new Gtk::Button());
  Gtk::HBox* hbox = Gtk::manage(new Gtk::HBox(false, 0));
  Gtk::Image *icon = Gtk::manage(new Gtk::Image(Gtk::Stock::ADD, Gtk::ICON_SIZE_MENU));
  icon->set_padding(5, 0); // set the padding X = 5, Y = 0
  hbox->pack_start (*icon, false, false);
  Gtk::Label *label = Gtk::manage(new Gtk::Label("Add"));
  label->set_padding(5, 0); // same padding, this makes 10 pixels between the icon and text label
  hbox->pack_start (*label, true, true);
  button->add(*hbox);
  show_all_children();

  return button;
}
[/PHP]

---

### Post by t1497f35 on 2012-06-13
> **hakermania said:**
> How about, instead of "Save" you give it "     Save" (with 2-3 spaces before the 1st letter)?
Thanks, but changing the label makes the icon go away.

The other example is nice but couldn't get the left alignment of the label & icon done.

---

### Post by r-senior on 2012-06-13
I don't think you should try and fix it. You'll just be inconsistent with everything else. It's the appearance of the stock GTK buttons in Ubuntu that's the problem and it ought to be reported as a bug. I tried the same thing on Gnome Shell in a Debian Wheezy VM and the spacing was OK.

---

### Post by t1497f35 on 2012-06-13
> **r-senior said:**
> I don't think you should try and fix it. You'll just be inconsistent with everything else. It's the appearance of the stock GTK buttons in Ubuntu that's the problem and it ought to be reported as a bug. I tried the same thing on Gnome Shell in a Debian Wheezy VM and the spacing was OK.
Sure.

---

