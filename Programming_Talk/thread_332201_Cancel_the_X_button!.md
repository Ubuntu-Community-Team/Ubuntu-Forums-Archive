---
title: "Cancel the X button!"
date: 2007-01-05
forum: Programming Talk
---

### Post by Ben Sprinkle on 2007-01-05
Anyone know how to cancel the clode action when usr clicks X?
I need to stop it so I can redirect it to another void before closing.

---

### Post by Engnome on 2007-01-05
What toolkit?

---

### Post by Ben Sprinkle on 2007-01-05
I just forgot to mention, gtkmm 2.4 ;)
I also need to know how to change the function of the maximize button.

---

### Post by Engnome on 2007-01-05
Well I don't know exactly how to do it with gtkmm but I can outline the steps.

You need to set up so that when user clicks X something will be called. If you are using glade this is easy select the window and add signal delete_event in the signals tab.

Not sure how to do it in gtkmm without glade. (In perl it looked like this: $window->signal_connect(delete_event => \&delete_event); )

The function that takes care of delete_event needs to return a boolean, TRUE and the window will not close and you can do your stuff then exit however you want.

This is how it worked with perl anyway... hope it helps!

---

### Post by Ben Sprinkle on 2007-01-05
Anyone else know? I am lost.

---

### Post by gummibaerchen on 2007-01-05
You should give more information.

As Engnome mentioned, do you use Glade?

---

### Post by cabalas on 2007-01-06
If I remember right (which I might not), if your window is a child of Gtk::Window all you should have to do is override the on_delete_event() function.  The maximize one I can't say I rightly know.

---

### Post by Ben Sprinkle on 2007-01-06
Hmm, if I use a deconstructor(class_s::~class_a), I am trying to show a dialog, but if I do that << then it like hides the entire form then shows the dialog which I dont want, I want it to cancel all delete functions untill I tell it to delete.

---

