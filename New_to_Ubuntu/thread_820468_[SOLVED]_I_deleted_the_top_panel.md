---
title: "[SOLVED] I deleted the top panel"
date: 2008-06-06
forum: New to Ubuntu
---

### Post by captgadget on 2008-06-06
and now I can't get it back. Can someone help me out here?

Thanx

---

### Post by skymera on 2008-06-06
What i do is

Right click bottom panel > New Panel

Then simply drag it to the top.

Right click it and click Add to Panel to put your menus back etc

---

### Post by captgadget on 2008-06-06
When I right click the bottom panel all I get is help or about panels.

---

### Post by ruffEdgz on 2008-06-06
Once you get back the top panel, if anything is missing like the menu bar or anything like that, you can simply right click on the top panel and click **'Add to Panel'** which will then give you options to place a menu bar, weather, clock, notification area, etc... 

This can also be done for the bottom panel as well (or any other panel on your Ubuntu Machine).

---

### Post by kaibob on 2008-06-06
> **captgadget said:**
> When I right click the bottom panel all I get is help or about panels.

Open the configuration editor and navigate to the following key:

/apps/panel/global/locked_down

If this key is checked, the panel's right-click menu will only contain "Help" and "About Panels." Uncheck this option to get the full right-click menu including the option "New Panel." If this doesn't work, then I'm not able to help.

---

### Post by captgadget on 2008-06-06
The problem is that I can't get a selection to create a panel.

---

### Post by _sphinx_ on 2008-06-06
I think you have not tried what kaibob has said. Any ways I can restate his points. Just type in the terminal.
```
gconf-editor
```
and follow the path that kaibob has stated. 
OR following is other trick that I have read somwhere that may be related to your problem.
```

gconftool-2 - -shutdown
rm -rf ~/.gconf/apps/panel
pkill gnome-panel

```
I am not sure as I have not test these steps on my pc. I am stating this steps for here:
[http://www.watchingthenet.com/restore-panels-in-ubuntu-back-to-their-default-settings.html](http://www.watchingthenet.com/restore-panels-in-ubuntu-back-to-their-default-settings.html)

---

### Post by ruffEdgz on 2008-06-06
As a side note, if you don't know how to open up the terminal without the panel at the top, just press Alt-F2 and that should bring up a Run Application window. From there, type in 'gnome-terminal' and that should bring the application up and running.

Then do what *_sphinx_* or *kaibob* said to check and then do what *skymera* then told you do to

---

### Post by captgadget on 2008-06-06
I followed this and it worked perfectly!!!
[http://ubuntuforums.org/showthread.php?t=819811&highlight=top+panel](http://ubuntuforums.org/showthread.php?t=819811&highlight=top+panel)

---

### Post by kastorakos84 on 2008-06-06
You can also try this one!

[http://ubuntuforums.org/showthread.php?t=820461&highlight=menu](http://ubuntuforums.org/showthread.php?t=820461&highlight=menu)

---

