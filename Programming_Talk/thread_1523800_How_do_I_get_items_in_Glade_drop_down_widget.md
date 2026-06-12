---
title: "How do I get items in Glade drop down widget?"
date: 2010-07-04
forum: Programming Talk
---

### Post by fallenshadow on 2010-07-04
What do I have to do to get items into a glade drop down list?

I have GTKmm code loading up the Glade interface but am unsure as to how I put items in the drop down widget.

---

### Post by fallenshadow on 2010-07-04
Im sure somebody has put in an item in a drop down box before.

Does anybody have something to chip in?

---

### Post by mcphargus on 2010-07-04
If you're using python, read on... for any other language, I'm useless.

I can't stress it enough, don't use glade to declare liststores or treestores in python. build your models in code (it's only a few lines). Use Glade for everything else though, because it really is a great piece of software.

What language are you working with?

Libglade makes some issues, its buggy, but if you're using gtk.builder() instead of libglade (like what [quickly]("https://wiki.ubuntu.com/Quickly") provides) you can get the combobox or dropdown object with builder.get_object('object_name_in_glade') and then use the object it provides to work things out.

If you're working with python and the object you're trying to populate is a combobox, check out [[COLOR="DarkRed"]the combobox class reference[/COLOR]]("http://library.gnome.org/devel/pygtk/stable/class-gtkcombobox.html").

You'll always need the [[COLOR="darkred"]ListStore() reference too[/COLOR]]("http://library.gnome.org/devel/pygtk/stable/class-gtkliststore.html").

Make the liststore with list_var = gtk.ListStore(field1_type, field2_type*) and then populate it with list_var.append(stuff)

*This would be a python primitive datatype (like str and int), or a gobject datatype (something like gobject.STRING). I've always had better luck with regular python datatypes though.

I've got a quickly project that uses comboboxen pretty extensively on launchpad at [launchpad.net/eesu]("http://launchpad.net/eesu"). It might have some tidbits that you can pick out to help you understand it all better.

---

### Post by fallenshadow on 2010-07-04
Thanks for your reply! I am using C++ as my language.

With Glade I am using GTK builder. So I guess I have to use C++ code for the items.... and then point Glade to those items somehow?

---

### Post by mcphargus on 2010-07-04
I've never used Glade with C++ before, so I can't give the best advice. I'd imagine if you can get access to the drop-down object and set its model, you'll have success. Most of the list-type items (drop-down, combobox, treeview) that I've worked with in GTK need to be updated dynamically, so I don't really like to build lists in Glade. (the code I posted updates comboboxes from a sqlite database).

I think the best answer to your question is that you have to point GTK to your items somehow, not Glade. GTK will take over in running your app.

Strange as it sounds, when I'm working in Glade, I leave a lot of things empty, knowing that my code will pick up where it needs to. 

Example: If I'm using webkit, I'll stick a frame into a vbox in glade, or I'll just access the vbox directly and add the widget. I'll never see either in Glade, but when the application runs, gtk sticks webkit in the hole I've made.

---

### Post by pbrane on 2010-07-04
if you are using Gtk::ComboBoxText you can do something like this:
```

  Gtk::ComboBoxText reason_combo;
  refBuilder->get_widget("reason_combobox", reason_combo);
    .
    .
    .
    .
  const char* reasons[] = {
    "Cheating",
    "Player Abuse",
    "Spamming",
    "NR",
    "Idle too long",
    0
  };
	
  gint k = 0;
  while (reasons[k]) {
    reason_combo.append_text(Glib::ustring(reasons[k++]));
  }

```

---

### Post by fallenshadow on 2010-07-05
Thanks pbrane but this code throws up alot of errors.

Is this GTKmm code or just C++ code? (or is there any difference)

---

### Post by pbrane on 2010-07-05
The code is snipped from working code. It is gtkmm. Gtkmm is the C++ language binding for Gtk, which is written in C. I replaced Gtk::ComboBox with Gtk::ComboBoxText. I should have just posted the entire function so you could see how I did that.


```

// In the class declaration;
// Unfortunately Glade Interface Builder does not support
// Gtk::ComboBoxText widgets. So we must supply our own.
Gtk::ComboBoxText player_combo;
Gtk::ComboBoxText reason_combo;

// In the class definition:
void myclass::replace_input_placeholders()
{
  // Glade Interface Designer 3 doesn't support Gtk::ComboTextBox, so....
  // Remove the placeholder Gtk::ComboBox and add a Gtk::ComboTextBox
  // We don't need the combobox and it's TreeModel, we just want to
  // display strings. These comboboxes are on the input_dialog widget.

  Gtk::VBox *box;
  refBuilder->get_widget("vbox3", box);
	
  Gtk::ComboBox *replace;
  refBuilder->get_widget("player_placeholder", replace);
	
  box->remove(*replace);
  box->pack_start(player_combo);
  box->reorder_child(player_combo, 1);
	
  refBuilder->get_widget("reason_placeholder", replace);
	
  box->remove(*replace);
  box->pack_start(reason_combo);
  box->reorder_child(reason_combo, 4);
	
  // populate the reason box, used in kicking and banning
  const char* reasons[] = {
    "Cheating",
    "Player Abuse",
    "Spamming",
    "NR",
    "Idle too long",
    "Team killing",
    "Inappropriate Callsign",
    "Language",
    0
  };
	
  gint k = 0;
  while (reasons[k]) {
    reason_combo.append_text(Glib::ustring(reasons[k++]));
  }
}

```
Sorry for the confusion.

---

### Post by fallenshadow on 2010-07-06
Hey pbrane... any chance you would like to make a contribution to an open source project? :)

I just need you to organize your code to make it actually work! (im hopeless with it)

The project is Xwii, in case you are wondering! You could be the second contributor to the project. ;)

If you are interested I can send you the overall section of code for you to make it work. (its very small btw)

---

### Post by pbrane on 2010-07-06
I'd be willing to take a look at it. Sure.

---

### Post by fallenshadow on 2010-07-07
Ok to make things easy ive added a section for you and others to easily download the code.

[http://www.photofiltre-lx.org/projects/xwii/download.html](http://www.photofiltre-lx.org/projects/xwii/download.html)

You can try one of two things:

1. Just get items to show in the combobox.

2. Read filenames from a directory and list them in the combobox. This is our final goal but may be too hard for you.

Even if you can't do anything thanks for trying to help us! :)

EDIT: Oh I nearly forgot the binary included is 64bit so you may need to compile again if you are on 32bit.

---

### Post by pbrane on 2010-07-07
We need another way to communicate, but for now, I have questions.
1. Why are you using libglade? You should be using Gtk::Builder.
2. Do you have to use a Gtk::ComboBoxEntry or can it be a Gtk::ComboBoxText?

---

### Post by fallenshadow on 2010-07-07
1. I thought we were using GtkBuilder... however my development partner did the initial Glade file so maybe not.

Shall I do a fresh copy of the UI with GtkBuilder for you?

2. The combobox does not need text to be entered/typed into it. I hope this answers that question.

---

### Post by fallenshadow on 2010-07-07
Ok I went ahead and made a copy of the UI with GtkBuilder.

However now the Gtkmm code won't bring up the new UI.

If you like you can contact me directly via e-mail and I can send you the GtkBuilder UI. My e-mail is available on that Xwii site. (Dylan)

I assume I will have to use different code to load the new UI if its possible with GTKmm.

EDIT: Now using GTKmm code for the loading of GtkBuilder files. Also uploaded to download location, won't compile into a working executable though.

---

### Post by pbrane on 2010-07-07
I have already done the conversion. Your code is written for libglade, won't work for gtk::builder xml code. I sent you what I wrote in an email.

---

### Post by fallenshadow on 2010-07-07
Solved! :D  Thank you!

---

