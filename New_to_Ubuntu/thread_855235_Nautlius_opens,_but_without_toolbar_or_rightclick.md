---
title: "Nautlius opens, but without toolbar or rightclick"
date: 2008-07-10
forum: New to Ubuntu
---

### Post by D_D_T on 2008-07-10
Hi,
Can anyone suggest what may be wrong and how to fix this? I'm having some problems with Nautilus.
It opens fine, and I can switch from browser to the other mode in "configuration editor" but I can't right-click on files (or on the desktop) and the toolbar at the top of nautilus windows has dissappeared (ie: File/Edit/View...). Keyboard shortcuts don't work either so I can't make new files or anything like that. It's really frustrating!
I haven't got a clue what could be wrong, and would really appreciate some help.
Thank you for your time.
D_D_T

---

### Post by NilsE on 2008-07-10
Go into the configuration editor (gconf-editor) and navigate to apps > nautilus > preferences and make sure the start with options for toolbar is checked. That may atleast get you back the file toolbar.  You can then check other settings to see what if anything else got turned off in the preferences.

---

### Post by D_D_T on 2008-07-10
I'm afraid that it is turned on. I tried to turn it off, and then turn it back on, but this didn't do anything either. Thank you for the suggestion though.

---

### Post by NilsE on 2008-07-10
Try and see if ALT-V in nautilus brings up the view menu and try to turn the toobar on from there.

Also, look around in the configuration editor under nautilus to see if there is an option to turn menus on and off.

---

### Post by D_D_T on 2008-07-10
Sorry, neither of those options worked. Alt-V did nothing, and I couldn't find anything in Config to turn on/off menus.

---

### Post by NilsE on 2008-07-10
The only other thing I can think of is to go into the configuration editor under apps > nautilus > preferences and make sure always_use_browser is checked.

If that does not do it try to re-install nautilus and see if that resets it.  Can't make it worse as long as you don't uninstall it.  Just select reinstall in Synaptic

---

