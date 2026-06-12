---
title: "GtkStatusIcon libnotify"
date: 2008-03-03
forum: Programming Talk
---

### Post by cvasilak on 2008-03-03
Hi there,
i am writing a small C program using GtkStatusIcon and libnotify. Although I have attached the GtkStatusIcon to notify when I run the program the popup message is far away from the status icon.

Any ideas why? Is it a known bug?

Here is a screenshot that demonstrates the problem:
[http://users.forthnet.gr/her/gvasilakis/Screenshot.png](http://users.forthnet.gr/her/gvasilakis/Screenshot.png)

And here is the code: ( I have modified a status icon example that I found somewhere on the net adding the libnotify dependency)

[http://users.forthnet.gr/her/gvasilakis/statusicontest.txt](http://users.forthnet.gr/her/gvasilakis/statusicontest.txt)

Thanks in advance
Christos

---

### Post by Can+~ on 2008-03-03
I can't help you with C+gtk/libnotify, but I know that in python there are two methods to adjust that:

1) attach_to_widget(widget)
2) set_hint("x", coordx)
 set_hint("y", coordy)

*edit*
Checking the pynotify:
```

     |  add_action(...)
     |  
     |  attach_to_status_icon(...)
     |  
     |  attach_to_widget(...)
     |  
     |  clear_actions(...)
     |  
     |  clear_hints(...)
     |  
     |  close(...)
     |  
     |  set_category(...)
     |  
     |  set_hint(...)
     |  
     |  set_hint_byte(...)
     |  
     |  set_hint_byte_array(...)
     |  
     |  set_hint_double(...)
     |  
     |  set_hint_int32(...)
     |  
     |  set_hint_string(...)
     |  
     |  set_icon_from_pixbuf(...)
     |  
     |  set_timeout(...)
     |  
     |  set_urgency(...)
     |  
     |  show(...)
     |  
     |  update(...)

```

I guess you want "attach_to_status_icon()".

---

### Post by pragmatine on 2008-03-03
you may need to call gtk_widget_show or similar on the tray icon before trying to create the attached notification...

---

### Post by cvasilak on 2008-03-04
OK, thanks all, I will have a look.

Christos

---

