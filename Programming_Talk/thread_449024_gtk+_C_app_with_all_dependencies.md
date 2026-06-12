---
title: "gtk+ C app with all dependencies"
date: 2007-05-19
forum: Programming Talk
---

### Post by bradleyd on 2007-05-19
Hello everyone,
I have been playing around with trying to compile all dependencies in executable. In python you can use Freeze. I think you can static link libs with gcc options, not sure. The big problem is I created app with glade and now the glade file has to be in same directory as app to run. Can I static link glade file into final binary?
Thanks in advance.
Brad

---

### Post by maddog39 on 2007-05-20
No as far as I know, you cant compile the glade file into the program statically. However you can embed something similar into your program using strings and the GtkUIManager. But I'm sure that their are probably work arounds for the glade file needing to be in the same directory as the executable.

---

