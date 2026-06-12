---
title: "[SOLVED] vim question"
date: 2008-07-10
forum: New to Ubuntu
---

### Post by muteXe on 2008-07-10
evening,
How do I paste stuff from the clipboard to something open in vim?  I tried opening a open office doc, and selecting all the text (ctrl+A), then copying it (ctrl+c).  I thought pressing 'p' in command mode pastes the clipboard contents but it just says "register empty" at the bottom of the vim terminal.

cheers,

mute

---

### Post by dracayr on 2008-07-10
In the terminal generally paste with Ctrl+shift+V or by clicking the middle mouse button (although that's a bit more complicated than simply pasting the clipboard).

EDIT: Oh, and if you want to keep your formatting and indenting, type 

:set paste

in the command mode. If you don't want the paste mode anymore:

:set nopaste

dracayr

---

### Post by muteXe on 2008-07-10
ctl+shift+v worked a treat.
thanks :)

---

