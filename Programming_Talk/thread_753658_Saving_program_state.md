---
title: "Saving program state"
date: 2008-04-12
forum: Programming Talk
---

### Post by zagieman on 2008-04-12
I have written a simple program using gtkmm which has a few check and text entry widgets. I am unsure how to make it so that when the program is closed, it resumes in the same state as when it was closed.

Would this involve a separate file that I need to write out to? If so how would I go about this?

---

### Post by Can+~ on 2008-04-13
Store a configuration file, in any format, a plain text can do the job prety easily, like:
[PHP]something=value[/PHP]

Read the file on start, then implement those values on the interface, there's loads of methods in gtk that are basically "set_widget_to_some_state". Probably there's a library out there that can do that job for you.

---

### Post by Wybiral on 2008-04-17
What language are you using?

---

