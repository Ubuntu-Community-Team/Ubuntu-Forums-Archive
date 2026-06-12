---
title: "Trim the filename like gedit"
date: 2007-01-07
forum: Programming Talk
---

### Post by Ben Sprinkle on 2007-01-07
In C++ using gtkmm:
```

title = file_open_dialog.get_filename().c_str();
set_title(title);

```
title is a ustring, how can I trim the filename to just show the ending file like hi.txt not /home/hi.txt etc.?

---

### Post by duff on 2007-01-07
whatever the glibmm equivlant of this is:

[http://developer.gnome.org/doc/API/2.0/glib/glib-Miscellaneous-Utility-Functions.html#g-path-get-basename](http://developer.gnome.org/doc/API/2.0/glib/glib-Miscellaneous-Utility-Functions.html#g-path-get-basename)

---

### Post by Ben Sprinkle on 2007-01-07
Thanks, I will try it out.
I owe you one. ;)

---

