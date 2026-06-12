---
title: "gtkmm add image to button."
date: 2007-05-11
forum: Programming Talk
---

### Post by shador on 2007-05-11
I want to add an image to a button with "void Gtk::Button::set_image  	(Widget & image)"

But I don't really understand what widget I'm supposed to include in the command. Could anyone maybe give me an example of how it is used?

---

### Post by jamescox84 on 2007-05-11
Gtk::Image I think is what your looking for.

```

Gtk::Image image("filename");
your_button.set_image(image);

```

I think something like that should work.

---

