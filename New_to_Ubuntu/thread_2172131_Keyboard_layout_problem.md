---
title: "Keyboard layout problem"
date: 2013-09-03
forum: New to Ubuntu
---

### Post by yuriy3 on 2013-09-03
Hi!
In case when I choose "Left Ctrl (to first layout), Right Ctrl (to last layout)" (I used to use this option in windows) for switching layout I can't use CTRL+x and Ctrl+&#1089; in terminal, ubuntu just writing "x" or "c".

---

### Post by deadflowr on 2013-09-03
Don't expect Windows keybindings to be used by all other operating systems.

To learn what the keyboard layouts are for the terminal, open the terminal(I assume you're using Ubuntu default setup)
Then go to EDIT in the menu and then Keyboard shortcuts.

Tip: In case you aren't used to the menu layout of Ubuntu, it uses a menu scheme called global menus, which place the menu at the top left side of the top panel. It hides until you call it or move the mouse over it.

---

### Post by whitesmith on 2013-09-03
If you install xbindkeys (Software Center) you can customize your bindings that way.
[Edit] d/l the configuration for it also (xbindkeys-config) and run that to get started.

---

### Post by yuriy3 on 2013-09-04
Thanks for the answers!
I think the problem not with terminal but with Ubuntu. For example, I can't use default CTRL+insert for clipboard copiyng in gedit or any text fields in browsers when I choose "[COLOR=#000000]Left Ctrl (to first layout), Right Ctrl (to last layout)".
Ubuntu just disable default CTRL behavior while it pressed.

[/COLOR]> **whitesmith said:**
> If you install xbindkeys (Software Center) you can customize your bindings that way.
[Edit] d/l the configuration for it also (xbindkeys-config) and run that to get started.

thanks! I will try it

---

### Post by grahammechanical on 2013-09-04
I use two keyboard layouts in Libreoffice. English (UK, extended Win keys) and Greek (extended). When I am using the English keyboard layout then Ctrl+C = copy; Ctrl+X = cut and Ctrl+V = paste but these key bindings do not work in the Greek keyboard layout. Try using a variation of the keyboard layout.

Also, keyboard short-cuts do not work in the terminal. We have to use the Edit menu that appears when we mouse over the left side of the top panel when the terminal is in focus (Click on the terminal window).

In that Edit menu there is an option called Keyboard Shortcuts. Click that option and you will see that Shift+Ctrl+C = Copy and Shift+Ctrl+V = paste for the terminal.

As someone has already said, do not expect Linux to work like Windows. With Linux/Ubuntu we have something much better than just a cheap copy of another operating system.

Regards.

---

### Post by yuriy3 on 2013-09-05
> **grahammechanical said:**
> I use two keyboard layouts in Libreoffice. English (UK, extended Win keys) and Greek (extended). When I am using the English keyboard layout then Ctrl+C = copy; Ctrl+X = cut and Ctrl+V = paste but these key bindings do not work in the Greek keyboard layout. Try using a variation of the keyboard layout.

Also, keyboard short-cuts do not work in the terminal. We have to use the Edit menu that appears when we mouse over the left side of the top panel when the terminal is in focus (Click on the terminal window).

In that Edit menu there is an option called Keyboard Shortcuts. Click that option and you will see that Shift+Ctrl+C = Copy and Shift+Ctrl+V = paste for the terminal.

As someone has already said, do not expect Linux to work like Windows. With Linux/Ubuntu we have something much better than just a cheap copy of another operating system.

Regards.

The problem appears only if I choose [COLOR=#000000]"[/COLOR][COLOR=#000000][COLOR=#000000]Left Ctrl (to first layout), Right Ctrl (to last layout)"[/COLOR][/COLOR] in other cases (for instance Ctrl+Shift) all shortcuts in terminal works well. So it does not depend on keyboard layout.

---

