---
title: "i lost my window borders!"
date: 2008-07-21
forum: New to Ubuntu
---

### Post by cpu_medic on 2008-07-21
ok so lastnight everything was working perfectly. i shut down and go to bed. wake up the next morning and my window borders are gone!(specificly the bar on top of the window with the close,minimize,maximize buttons on it) does any body have any ideas what i did to break it and how would i fix it?

---

### Post by RomeReactor on 2008-07-21
Hi. If you're using Compiz, disabling it will return the window borders; if you want to keep Compiz running, press ALT+F2 and paste:
```
gtk-window-decorator --replace
```
and press enter. Are you also using Emerald?

---

### Post by tjwoosta on 2008-07-21
stupid question i guess but have you tried just rebooting?

sometimes on my computer some things will fail to load at boot and simply rebooting does the trick

---

### Post by ChildOfMana on 2008-07-21
If you have 'Compiz-Fusion Icon' installed (available from synaptic) load it up (from Applications > System Tools) and it should appear in your task bar (in the top right on a default installation).

Now simply right-click on it and go to 'Select Window Decorator' and choose either 'GTK Window Decorator' or 'Emerald' (depending on which you're using).

Should solve your problem (if you're using Compiz-Fusion anyway) :)

---

### Post by cpu_medic on 2008-07-22
i have rebooted multiple times and it still doesnt come up. also the above method diddnt work.

---

### Post by tel93 on 2008-07-22
2 questions:

1. Can you move windows using Alt+Drag?
2. Are you using Compiz?

---

### Post by sailor2001 on 2008-07-22
alt/f11 might have to click that a couple times

---

### Post by tel93 on 2008-07-22
> **sailor2001 said:**
> alt/f11 might have to click that a couple times
why?

to the OP. My guess is that you have the "Widget Layer" Compiz plugin enabled. Open ComizConfig Settings Manager and un-tick the plugin.

---

### Post by RomeReactor on 2008-07-22
> **cpu_medic said:**
> i have rebooted multiple times and it still doesnt come up. also the above method diddnt work.

You haven't told us yet if you have Compiz enabled, and whether you're using Emerald or not. If this only happens with Compiz enabled, and if you have compizconfig-settings-manager installed, open it, go to the 'Effects' section, and make sure the 'Window Decoration' plugin is enabled.

EDIT: Also try resetting ccsm to default by going to its preferences.

---

### Post by UltraCheese on 2008-07-22
I'm kinda new to this so I might just be giving a stupid answer, but wouldn't running gnome-wm get it back?

---

### Post by billynomates on 2008-07-22
```
emerald --replace
```?

If that works, add it to your sessions.

---

### Post by philinux on 2008-07-22
System>Prefs>Advanced Desktop effects.

Click the effects category.

If the windows decoration box is ticked then untick and tick again.

If not ticked then tick it.

---

### Post by tsmets on 2008-09-11
In my case, the screen freezed yesterday eve and I lost all the windows decorations

[IMG]http://tsmets.lautre.net/img/Lost_window_decoration.jpeg[/IMG]

To solve it :
System
[INDENT]  --> Preferences
[INDENT]      --> Appearance[/INDENT][/INDENT]

I selected another "Theme", then the original one and it was all OK

\T,

---

