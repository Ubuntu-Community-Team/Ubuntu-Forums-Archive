---
title: "easy MonoDevelop question (i hope!)"
date: 2008-07-28
forum: Programming Talk
---

### Post by PetePete on 2008-07-28
when creating a GUI, there is the designer view with the toolbox, well i've managed to delete the vbox container and a widget (can't remember which one)

anyway to restore them?

thanks

---

### Post by clash on 2008-07-28
Ctrl + Z will undo so much

---

### Post by PetePete on 2008-07-29
tried that at the time. didn't work.
anyway i've closed the app now. 

still not there.

---

### Post by gwi on 2008-08-12
I just did the same with the Entry (textbox) widget. It is no longer in the toolbox. How can I restore it?

@clash:
PetePete and I did not accidentally remove a widget from a designer window, but from the toolbox. Just press Delete when the toolbox has the focus, and instead of removing the selected widget from the designer window, it is silently removed from the toolbox. Ctrl-Z does nothing there.

---

### Post by PetePete on 2008-08-12
I deleted a config file in my home dir which then restores the toolbar to defaults.

i THINK it was this file

~/.config/MonoDevelop/Toolbar.xml

I spoke to one of the devs on Irc about it and said he was going to file it as a bug.

---

### Post by gwi on 2008-08-12
That's it! Thanks.

Actually I just (before reading your reply) replaced Toolbox.xml with the original one (which was created after installing MonoDevelop, and which was in a backup I made). This just contains an empty list
```
<ToolboxList />
```, with the same result: the list is re-created when MonoDevelop is started.

---

### Post by incubii on 2008-10-20
> **PetePete said:**
> I deleted a config file in my home dir which then restores the toolbar to defaults.

i THINK it was this file

~/.config/MonoDevelop/Toolbar.xml

I spoke to one of the devs on Irc about it and said he was going to file it as a bug.

Deleting that file fixed my issue when i deleted the menubar

---

