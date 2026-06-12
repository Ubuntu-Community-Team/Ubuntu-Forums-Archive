---
title: "[C++]gtkmm: Changing color of a label"
date: 2006-05-30
forum: Programming Talk
---

### Post by trigeorgis on 2006-05-30
Hello guys,

This is my code:
```

Gdk::Color c( "red" );
window1->text->modify_bg(Gtk::STATE_NORMAL, c );

```

but the label still remains gray :(
[SIZE="2"]
im new to gtk, any help? ohh and any good tutorials? :p[/SIZE]

---

### Post by trigeorgis on 2006-05-30
ok, i found out that i had to add an eventbox, althought i cant understand why :p

---

