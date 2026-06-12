---
title: "AnJuta Code Folding dont work???"
date: 2009-10-09
forum: Programming Talk
---

### Post by Face_Man on 2009-10-09
Hello all, 
how to get the code folding work on AnJuta ? when i google it i found that code folding only work with Scintilla-based editor. therefore i install scite but it did not work.

Any help would be much appreciated.
Anjuta 2.28.0.0

---

### Post by MadCow108 on 2009-10-09
scintilla is included in anjunta
you have to change the editor used in the preferences:
edit->preferences->general->prefered plugin
mark you're currently used plugin and klick forget selected plugin

now it will ask you at startup which editor plugin you want to use, there select scintilla

---

### Post by Face_Man on 2009-10-09
> **MadCow108 said:**
> scintilla is included in anjunta
you have to change the editor used in the preferences:
edit->preferences->general->prefered plugin
mark you're currently used plugin and klick forget selected plugin

now it will ask you at startup which editor plugin you want to use, there select scintilla

forget selected plugin button is disable!

---

### Post by MadCow108 on 2009-10-09
edit: just saw that in the current version scintilla seems to be removed from trunk
so you probably have to load the extra packages: [http://projects.gnome.org/anjuta/downloads.shtml](http://projects.gnome.org/anjuta/downloads.shtml)



does the scintilla plugin it show in the installed plugins tab? (when disabling "show only user activatable plugins")

did you compile anjuta from source? if yes you may have to build it with scintilla plugin enabled:
./configure --enable-plugin-scintilla

---

### Post by Face_Man on 2009-10-10
> **MadCow108 said:**
> edit: just saw that in the current version scintilla seems to be removed from trunk
so you probably have to load the extra packages: [http://projects.gnome.org/anjuta/downloads.shtml](http://projects.gnome.org/anjuta/downloads.shtml)



does the scintilla plugin it show in the installed plugins tab? (when disabling "show only user activatable plugins")

did you compile anjuta from source? if yes you may have to build it with scintilla plugin enabled:
./configure --enable-plugin-scintilla

didnot work
unrecognized command - something like that

---

### Post by MadCow108 on 2009-10-10
yes I realized that...
load the extra packages and install it manually

---

### Post by Face_Man on 2009-10-10
> **MadCow108 said:**
> 
load the extra packages and install it manually

Work great, thx for the help.

---

### Post by yotama9 on 2010-08-20
Hi. I tries to install the plugin extra package but got the following error:

[HTML]plugin.c:185: error: ‘IANJUTA_PROJECT_MANAGER_TARGET_EXECUTABLE’ undeclared (first use in this function)
[/HTML]

What does it mean?

Thanks

---

