---
title: "Emerald"
date: 2008-06-08
forum: New to Ubuntu
---

### Post by pmq on 2008-06-08
Ok, i wanted to do something nice with my desktop, so i downloaded a nice theme from gnome-look.org. It was an emerald theme, so i did the logical thing and downloaded + installed emerald.
After importing the file, nothing happened, i was scratching my head for a bit then just typed emerald into the terminal.
I was pleased to see the theme described appear on my screen, well, i expected more, i didnt think "theme" meant just a border colour. 
Anyway, once i closed terminal the entire border for all my windows disappeared. I freaked and had to run emerald in the terminal again and everything was restore.

I guess my question is, does terminal have to be running constantly in order for me to have a fancy theme?

---

### Post by powerpleb on 2008-06-08
> **pmq said:**
> Ok, i wanted to do something nice with my desktop, so i downloaded a nice theme from gnome-look.org. It was an emerald theme, so i did the logical thing and downloaded + installed emerald.
After importing the file, nothing happened, i was scratching my head for a bit then just typed emerald into the terminal.
I was pleased to see the theme described appear on my screen, well, i expected more, i didnt think "theme" meant just a border colour. 
Anyway, once i closed terminal the entire border for all my windows disappeared. I freaked and had to run emerald in the terminal again and everything was restore.

I guess my question is, does terminal have to be running constantly in order for me to have a fancy theme?

No definitely not...
Try this:
```
emerald --replace
```

---

### Post by pmq on 2008-06-08
Nope, still steals my borders when i close terminal
:(

---

### Post by Grishka on 2008-06-08
no man, install fusion-icon and put it in your autostart or run from Alt+F2 menu. this will take care of that. also, emerald is a windows decorations engine, so it mainly affects window borders.

---

### Post by stalkier on 2008-06-08
> **Grishka said:**
> no man, install fusion-icon and put it in your autostart or run from Alt+F2 menu. this will take care of that. also, emerald is a windows decorations engine, so it mainly affects window borders.

I have to agree with you. Emerald should be installed along with CCSM and fusion-icon. These can all be found in the Syaptics Package Manager and clicking search - type compiz. You can also add Screenlets and SimDock if you would like. 

After these are installed just start Fusion-icon via Applications - System Tools - Fusion-Icon. Right Click the icon on the taskbar - Choose Window Decorator - click Emerald. It SHOULD be started automatically for now on. If you need to change the settings just start Fusion-icon again and change it.

I hope this helps.

---

### Post by Grishka on 2008-06-08
what he said. :) but ccsm may be too hardcore for some users. try simple-ccsm if you can't find your way through all ccsm options.

---

### Post by pmq on 2008-06-08
Thanks, i think i will try this eventually, but now im just ready to let my head explode. There seems to be alot to look at. I thought changing the menus, icons, borders, widgets etc, would be as easy as setting a compiz effect or setting a background, but nothing is simple i guess. 
I just got ride of the themes i downloaded and uninstalled emerald, after a reboot, my borders returned.
Are there any simple step by step tutorials i could read through before i start jumping about with settings?

---

### Post by Grishka on 2008-06-08
> **pmq said:**
> Thanks, i think i will try this eventually, but now im just ready to let my head explode. There seems to be alot to look at. I thought changing the menus, icons, borders, widgets etc, would be as easy as setting a compiz effect or setting a background, but nothing is simple i guess. 
I just got ride of the themes i downloaded and uninstalled emerald, after a reboot, my borders returned.
Are there any simple step by step tutorials i could read through before i start jumping about with settings?

tutorials for what? there are many various kinds of menus, window borders, widgets, gadgets, docks and stuff. but you didn't have to remove those themes you got, you were almost there. :) reinstall emerald and install fusion-icon. this will let you manipulate compiz in a most effective way that is currently possible. your window borders were gone, because when you close the terminal, the application that you run in it also quits. that's why should run such programs through the menus, or by pressing Alt+F2 and finding the program there.

---

