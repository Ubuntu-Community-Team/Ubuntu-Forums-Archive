---
title: "[SOLVED] Keyboard shortcut keys"
date: 2008-10-10
forum: New to Ubuntu
---

### Post by Eto_Demerzel on 2008-10-10
Two questions:

1) Is there any way to reset all keyboard shortcuts to default? 

2) I set a certain key combination to open terminal (Alt F5). I didn't do it simply through System>Prefs>Keyboard shortcuts, I seem to remember that I edited something in two places, but I can't remember where! Now I want to change that shortcut but I don't know how. The Run a terminal option in System>Prefs>Keyboard shortcuts is disabled. But of course, pressing Alt F5 anywhere brings up the terminal.

Does anyone know what I did to get this shortcut working and how to change it?

Thanks.

---

### Post by drs305 on 2008-10-10
If you changed two settings you probably did it through gconf-editor.

Run "gconf-editor" and then go to /apps/metacity/keybinding_commands (look for the specific run_command) and global_keybindings to see if that's where you may have bound the shortcut.

---

### Post by Eto_Demerzel on 2008-10-10
Yeah, that's right, I did it in gconf-editor. 

Thanks a lot. I wonder how many hours I'd spend trying to remember/figure out where I did it. :)

---

