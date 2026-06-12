---
title: "Ruby Gtk::Table"
date: 2007-06-11
forum: Programming Talk
---

### Post by apoth on 2007-06-11
I've tried creating an application with a Gtk::Table and want to add data to it dynamically.

```
symbol_label = Gtk::Label.new.set_text('Test1')
price_label = Gtk::Label.new.set_text('Test2')
@glade.get_widget("table1").attach_defaults(symbol_label,0,1,0,1)
@glade.get_widget("table1").attach_defaults(price_label,1,2,0,1)
```

The above code runs without error, but doesn't visibly add rows to the table. There aren't any rows in the table so I don't know if anything is perhaps just not visible. Perhaps I need to call some sort of repaint method? Anyone know where I might be going wrong?

Thanks

---

### Post by apoth on 2007-06-11
I just had to explicitly .show the labels.

---

