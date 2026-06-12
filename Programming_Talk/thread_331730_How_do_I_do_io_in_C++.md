---
title: "How do I do i/o in C++?"
date: 2007-01-05
forum: Programming Talk
---

### Post by Ben Sprinkle on 2007-01-05
I am using gtkmm for m C++ wrapper, how would I make an input buffer?
My void looks like this:
```

void class_a::open_clicked() {

	Gtk::FileChooserDialog file_open_dialog("Open File...", Gtk::FILE_CHOOSER_ACTION_OPEN);

	file_open_dialog.set_transient_for(*this);

	file_open_dialog.add_button(Gtk::Stock::CANCEL, Gtk::RESPONSE_CANCEL);

	file_open_dialog.add_button(Gtk::Stock::OPEN, Gtk::RESPONSE_OK);

	Gtk::FileFilter filter_all;

	filter_all.set_name("All Files");

	filter_all.add_pattern("*");

	file_open_dialog.add_filter(filter_all);

	int choice = file_open_dialog.run();

	switch(choice) {

		case(Gtk::RESPONSE_OK): {

			break;

		} case(Gtk::RESPONSE_CANCEL): {

			break;

		} default: {

			cout << "Unexpected button clicked" << endl;

			break;

		}

	}

}

```
A simple ifstream won't work. :(

---

### Post by cabalas on 2007-01-05
Now I'm going to go out on a limb and presume that you are trying to load a text file here and display it in a Gtk::TextView in that case I would just do, (I would have the Gtk::TextView declared else where, for sake of post I'm going to call it mText):

```

Glib::usting buf;
char ch;

std::ifstream file(file_open_dialog.get_filename().c_str());

if(file.fail()) return;

while(!file.eof()) {
  file.get(ch);
  
  if(!file.fail()) {
    buf += ch;
  }
}

file.close();
mText.get_buffer()->set_text(buf);


```

I'm sure there is probably a nicer way to do this using vfsmm but I haven't gotten around to learning it yet, and also note some of my syntax maybe wrong I didn't bother to pull up the gtkmm reference.

Hope that helps

---

### Post by Ben Sprinkle on 2007-01-05
Oh wow, thanks a crap load. I was reading about some other complicated *** way to do it which was like 50 lines long. Thanks!

---

