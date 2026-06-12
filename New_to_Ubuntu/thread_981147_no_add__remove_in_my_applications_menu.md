---
title: "no add / remove in my applications menu???"
date: 2008-11-13
forum: New to Ubuntu
---

### Post by the ig on 2008-11-13
can't find my add / remove application item in the usual place, 'APPLICATIONS' - ubuntu help told me to look there.
can't get going with anything without this. 
am i looking in the wrong place on desktop?
any obvious reasons why it could be missing?
how can i get the missing add / remove item?

thanks in advance,
lawrence.

---

### Post by tuxsheadache on 2008-11-13
Try looking in System-Preferences-Main Menu and see if it's been disabled

---

### Post by LowSky on 2008-11-13
You could always use synaptic or the command line?

What application are you looking to install we can help

---

### Post by oldos2er on 2008-11-13
Use System, Administration, Synaptic Package Manager instead.

---

### Post by MasterSander on 2008-11-13
Just right click your menu bar and select edit menu, enable it there.

---

### Post by the ig on 2008-11-13
hi, 
thanks for your replies.
i went into System Preferences - Main Menu, and indeed found that Add / Remove was disabled, (no tick in 'Show' column next to Add / Remove item). 
i tried to tick it's box but the tick would disappear after 2 seconds.

also, when right clicking my menu bar i could not see an 'Edit Menu' option.

i have yet to try the other suggestions.

best,
l.

---

### Post by ugm6hr on 2008-11-13
Try "Alt+F2":
/usr/bin/gnome-app-install

That should start it.

If it doesn't work, install the [application]("apt:gnome-app-install").

---

