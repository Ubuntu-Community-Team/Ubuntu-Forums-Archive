---
title: "saving screenshots (changing the default)"
date: 2013-05-12
forum: New to Ubuntu
---

### Post by mystmaiden on 2013-05-12
Hi, I have a couple of questions about changing the default folder for screenshots. I really don't want them going to Pictures. How can I change it? Also, must it be a directory or can I use a folder on my Desktop for instance?
I am running Precise classic no tweaks.

Thanks,
mystmaiden

---

### Post by hansdown on 2013-05-12
Hi,
mystmaiden

Open the screenshot app, and in the top left, click

> edit> preferences.

Under the "save screenshots to...", You should be able to change to desktop, etc.

---

### Post by mystmaiden on 2013-05-13
When I open the screenshot app, there isn't any edit/preferences option. I can use it instead of the print screen button and save to a specific folder. Is there a way to make the Print Screen button work the same way?

---

### Post by Frogs Hair on 2013-05-13
When the screen shot tool is used and open prior to saving you will see a drop-down directory menu. On the bottom of the menu you will see the other option and you can select desktop. The print screen key will send to pictures automatically unless you use the tool from  the menu.

You could give Shutter from the software center a try , but the print screen key might use the default tool.

---

### Post by mc4man on 2013-05-13
You can check & see if setting an autosave location in dconf-editor works in 12.04, it may not or may need some finagling to work, probably the latter. Also being in a gnome-session may be a bit different than unity session, you may not get the confirm location box ?? (if so then  all the more reason to be able to edit the autosave location

It does in 13.04 as seen in screen, I first set autosave to Desktop in dconf-editor, then pressed print key. Desktop was auto-selected in the confirm box.

---

