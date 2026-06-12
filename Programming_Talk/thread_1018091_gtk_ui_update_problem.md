---
title: "gtk ui update problem"
date: 2008-12-21
forum: Programming Talk
---

### Post by blake82 on 2008-12-21
Hi,

I'm having a frustrating gtk problem

I have an external hardware controller with a bunch of knobs, and I have a gtk gui that I need to reflect the state of the controller.

My problem is with the gui refresh.

whenever there is a change on the controller, it calls:
```

gtk_range_set_value(GTK_RANGE(controller)
```

unfortunately, the gui only refreshes every two seconds for some reason when I do that. So I've set the function to also call:
```

Gdk::Window::process_all_updates();
```

This works much better, but the gui will regularly hang for a second or two with this method.

I've been trying to find a cause for this *all day long*, but I can't figure it out. I'm fairly new to gtk, so I'm assuming there's probably something simple I'm not doing.

Any ideas?

---

### Post by blake82 on 2008-12-21
oh, forgot to mention.

I'm using c++

---

### Post by days_of_ruin on 2008-12-21
C++? That first code block looks like C.

Also you didn't add any functions to the "idle" thread did you?

---

### Post by blake82 on 2008-12-22
No... not that I know of at least.

---

