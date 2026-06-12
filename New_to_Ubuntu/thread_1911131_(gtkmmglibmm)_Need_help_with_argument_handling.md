---
title: "(gtkmm/glibmm) Need help with argument handling"
date: 2012-01-18
forum: New to Ubuntu
---

### Post by d2btoo on 2012-01-18
Hello,

I need some help with my program(using gtkmm) which now need to parse command-line arguments, the problem is I couldn't find any guides/tutorial regarding glibmm, the ref/documentation is very limited... so just hoping anyone here might give me a good link to guides, idea etc. 

thanks!

PS: It seems basicaly I have to deal with **Glib::OptionContext**, **Glib::OptionGroup** and **Glib::OptionEntry** classes, but how to use them correctly is a mistry!, especially the function **void Glib::OptionGroup::add_entry(const OptionEntry& entry)** giving me nightmares(segfaults) :confused:

EDIT: solved now!

---

