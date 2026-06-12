---
title: "[Python/Pygtk]How to show window transition"
date: 2011-06-25
forum: Programming Talk
---

### Post by Dhiraj Thakur(Invincible) on 2011-06-25
I want to display a window with some widgets and when user presses a button the widgets in the window change and the same window remains with new widgets in the window...i want to achieve this transition in pygtk can i do that????.....pllzzz....hellp

Thanks in advance..!!

---

### Post by Neezer on 2011-06-25
> **Dhiraj Thakur(Invincible) said:**
> I want to display a window with some widgets and when user presses a button the widgets in the window change and the same window remains with new widgets in the window...i want to achieve this transition in pygtk can i do that????.....pllzzz....hellp

Thanks in advance..!!

I'm not too  familiar with this, but I'd try creating a function that repacks the window when the function is called. Then assign that function to the button that you want.

---

### Post by yotam on 2011-06-25
Define and set all widgets from start.
But call show() and hide() before the actual gtk.main()
according to what you want to be shown in the beginning.

In the button callback, you can call show()
on some of the hidden widgets.

---

