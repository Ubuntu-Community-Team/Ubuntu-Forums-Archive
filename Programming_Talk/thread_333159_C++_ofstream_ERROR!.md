---
title: "C++ ofstream ERROR!"
date: 2007-01-07
forum: Programming Talk
---

### Post by Ben Sprinkle on 2007-01-07
When trying to compile my program I get this:
```

~/Desktop$ g++-4.1 class_a.cc `pkg-config gtkmm-2.4 --cflags --libs`
class_a.cc: In member function ‘virtual void class_a::save_as_clicked()’:
class_a.cc:221: error: jump to case label
class_a.cc:218: error:   crosses initialization of ‘std::ofstream save_file’
class_a.cc:223: error: jump to case label
class_a.cc:218: error:   crosses initialization of ‘std::ofstream save_file’

```
My virtual void looks like this:
```

void class_a::save_as_clicked() {
	Gtk::FileChooserDialog file_save_dialog("Save As...", Gtk::FILE_CHOOSER_ACTION_SAVE);
	file_save_dialog.set_transient_for(*this);

	file_save_dialog.add_button(Gtk::Stock::CANCEL, Gtk::RESPONSE_CANCEL);

	file_save_dialog.add_button(Gtk::Stock::SAVE, Gtk::RESPONSE_OK);

	int choice = file_save_dialog.run();

	switch(choice) {

		case(Gtk::RESPONSE_OK):
			ofstream save_file(file_save_dialog.get_filename().c_str());
			save_file << text_view.get_buffer()->get_text();
			break;

		case(Gtk::RESPONSE_CANCEL):
			break;

		default:

			cout << "Unexpected button clicked" << endl;

			break;

		}

}

```
What's wrong??

---

### Post by xtacocorex on 2007-01-07
Do you have this at the top of your code?
```
using namespace std;
```If not, you need to change the stuff in the std library to use that so the last part of your code would be:
```

    switch(choice) {

        case(Gtk::RESPONSE_OK):
            ofstream save_file(file_save_dialog.get_filename().c_str());
            save_file << text_view.get_buffer()->get_text();
            break;

        case(Gtk::RESPONSE_CANCEL):
            break;

        default:

            std::cout << "Unexpected button clicked" << std::endl;

            break;

        }

```
I don't know if anything else is wrong as I haven't done any GTK programming in C/C++.

---

### Post by Ben Sprinkle on 2007-01-07
I have the namespace at the top, yes.
Anone else know?

---

### Post by Ansible on 2007-01-07
Its not an ofstream problem; its just that in C++ you aren't allowed to create any vars in a switch statement like that.  If this kind of thing was allowed then you might try to use 'save_file' in your cancel or default cases, but at that point it would not be initialized because the OK case wasn't executed.  Same goes for any var, ints, strings, whatever.  

Anyway, you can fix it by enclosing your first case in brackets, like this:

```

    switch(choice) {

        case(Gtk::RESPONSE_OK):
        {
            ofstream save_file(file_save_dialog.get_filename().c_str());
            save_file << text_view.get_buffer()->get_text();
            break;
        }
        case(Gtk::RESPONSE_CANCEL):
            break;

        default:

            std::cout << "Unexpected button clicked" << std::endl;

            break;

        }

```

---

### Post by Ben Sprinkle on 2007-01-07
> **Ansible said:**
> Its not an ofstream problem; its just that in C++ you aren't allowed to create any vars in a switch statement like that.  If this kind of thing was allowed then you might try to use 'save_file' in your cancel or default cases, but at that point it would not be initialized because the OK case wasn't executed.  Same goes for any var, ints, strings, whatever.  

Anyway, you can fix it by enclosing your first case in brackets, like this:

```

    switch(choice) {

        case(Gtk::RESPONSE_OK):
        {
            ofstream save_file(file_save_dialog.get_filename().c_str());
            save_file << text_view.get_buffer()->get_text();
            break;
        }
        case(Gtk::RESPONSE_CANCEL):
            break;

        default:

            std::cout << "Unexpected button clicked" << std::endl;

            break;

        }

```
I thank you.

---

