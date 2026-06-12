---
title: "Eclipse and Darklooks Theme"
date: 2010-09-11
forum: Programming Talk
---

### Post by misha680 on 2010-09-11
I need to use Eclipse for my work on the OpenMRS project as most developers use it.

I have been struggling not just to find a dark color scheme for Eclipse:
[http://stackoverflow.com/questions/120621/dark-color-scheme-for-eclipse](http://stackoverflow.com/questions/120621/dark-color-scheme-for-eclipse)
[http://stackoverflow.com/questions/96981/color-themes-for-eclipse](http://stackoverflow.com/questions/96981/color-themes-for-eclipse)

or even to write a plug-in to change colors:
[http://stackoverflow.com/questions/3681206/changing-eclipse-colors-from-a-plug-in-where-can-i-change-e-g-java-editor](http://stackoverflow.com/questions/3681206/changing-eclipse-colors-from-a-plug-in-where-can-i-change-e-g-java-editor)
[http://old.nabble.com/Theming-eclipse-JDT-td29677631.html](http://old.nabble.com/Theming-eclipse-JDT-td29677631.html)

The problem:
Even if one changes colors in General -> Appearance, one needs to change colors for each _new_ plugin.

Some colors do not seem to be changeable, even with gnome-color-chooser.

Finally, I found a simple solution.

This _does not_ result in a dark color scheme for Eclipse, but results in an Eclipse where I _can read_ all the text!

Applications->Accessories->Terminal
```

mkdir -p ~/bin
touch ~/bin/eclipse
chmod 755 ~/bin/eclipse
gedit ~/bin/eclipse

```
Copy and paste the following text _if you are using eclipse from repositories_:
```

#!/bin/bash
GTK2_RC_FILES=/usr/share/themes/Clearlooks/gtk-2.0/gtkrc /usr/bin/eclipse

```
If you have eclipse in another location (e.g., ~/opt/eclipse/eclipse), be sure to replace /usr/bin/eclipse with the relevant location.

Thank you!
Misha

---

