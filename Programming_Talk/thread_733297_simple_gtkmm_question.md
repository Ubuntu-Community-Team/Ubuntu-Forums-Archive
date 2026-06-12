---
title: "simple gtkmm question"
date: 2008-03-23
forum: Programming Talk
---

### Post by SledgeHammer_999 on 2008-03-23
I started using gtkmm. I came across some functions which take as parameters some enums. These enums point to his page of the documentation->[link](http://gtkmm.org/docs/gtkmm-2.4/docs/reference/html/group__gtkmmEnums.html)

But my problem is that it doesn't tell which header I need to "#include"  and I am unable to use any enum.

Do you know what should I do?

---

### Post by SledgeHammer_999 on 2008-03-23
The problem is somewhere else. Maybe I don't understand how to use enumerations. The compiler doesn't complain about the 'type of the enum' but for the value I am trying to assign to the enumeration.This means that it already 'knows' about the enumeration I am using. Here's an example:
```
Gtk::FileChooserAction d = FILE_CHOOSER_ACTION_OPEN;
```

Here's the error I get:
```
error: &#8216;FILE_CHOOSER_ACTION_OPEN&#8217; was not declared in this scope
```

---

### Post by WW on 2008-03-23
Try
```
Gtk::FileChooserAction d = Gtk::FILE_CHOOSER_ACTION_OPEN;
```

---

### Post by SledgeHammer_999 on 2008-03-24
Thank you. I can't believe that it was so simple.

---

