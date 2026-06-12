---
title: "Rerunning ruby-glade-create-template"
date: 2007-06-09
forum: Programming Talk
---

### Post by apoth on 2007-06-09
If I create a complicated UI and need to make a change to it down the line, currently I have to rerun ruby-glade-create-template and add in all the 'glue' code again for the callbacks to link to the 'business logic'.

Is there a way of regenerating the glade file and keeping the glue code where I've left widgets otherwise untouched? It'd be really useful if there is.

Thanks

---

### Post by marcantonio on 2007-09-09
You don't have to rerun ruby-glade-create-template every time you make a change to the gui.  Glade only updates the .glade file.  You will have to add callbacks, but they are simple method declarations.

HTH
Marc

---

### Post by charlie763 on 2008-04-13
Try [Gladex]("https://launchpad.net/gladex/"). It has a GUI, supports ruby code generation. I also believe it keeps the GUI code and your callback code in two different files and will append the callback file when you add a new callback to the glade file.

---

