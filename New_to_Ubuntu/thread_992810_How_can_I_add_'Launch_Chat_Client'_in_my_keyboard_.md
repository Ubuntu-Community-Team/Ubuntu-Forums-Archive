---
title: "How can I add 'Launch Chat Client' in my keyboard shortcuts"
date: 2008-11-25
forum: New to Ubuntu
---

### Post by crjackson on 2008-11-25
I have a Logitech Internet/media keyboard that seems to be fully supported for every single button except the 'Messenger' button. Looking in the Keyboard Shortcuts GUI I find everything except that one item.

Is there a file I can edit to add that particular option and assign the intended key?

Thanks for any help.

---

### Post by Elfy on 2008-11-25
I added a similar command to my calculator button - 

First run xev from a terminal to determine it's name - in my case the button was called
XF86Calculator

Open gconf-editor - navigate to apps/metacity

In global_keybindings - I mapped run_command_1 to XF86Calculator - double click to let it edit
In keybinding_commands - I added  /usr/bin/xchat - dbl click to edit

Hope that helps

---

### Post by crjackson on 2008-11-25
Thanks, xev doesn't detect the key when pressed so I guess it isn't going to happen. Would have been cool, but no big dean then.

---

### Post by Elfy on 2008-11-25
Had a bit of a dig - try using XF86Messenger

---

### Post by crjackson on 2008-11-25
> **forestpixie said:**
> Had a bit of a dig - try using XF86Messenger


Okay, I'll give it a shot tomorrow. I'm at work right now...

---

