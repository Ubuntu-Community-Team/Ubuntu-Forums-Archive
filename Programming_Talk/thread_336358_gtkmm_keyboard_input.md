---
title: "gtkmm keyboard input"
date: 2007-01-11
forum: Programming Talk
---

### Post by evster on 2007-01-11
Hello,

I am writing my first gtkmm program.  I have made many gui programs in other languages (mostly on windows), but I am having trouble figuring out how to get keyboard events.  For example, if someone presses 'esc' i want the program to exit.  Could anyone point me to some examples of this?

Thanks!
evster

---

### Post by jblebrun on 2007-01-11
Have you learned about signals in GTK, yet? What you probably want is a keypress_event sort of signal Check out the gtkmm docs and search around for more information about signals:

[http://www.gtkmm.org/docs/gtkmm-2.4/docs/](http://www.gtkmm.org/docs/gtkmm-2.4/docs/)
[http://www.gtkmm.org/docs/gtkmm-2.4/docs/tutorial/html/apb.html](http://www.gtkmm.org/docs/gtkmm-2.4/docs/tutorial/html/apb.html)

---

