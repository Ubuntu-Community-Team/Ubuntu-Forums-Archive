---
title: "[SOLVED] Editing the main menu help"
date: 2008-11-26
forum: New to Ubuntu
---

### Post by KuroYoma on 2008-11-26
I am running Xubuntu 8.10 and have entries from wine in my Applications-> Others menu of applications that are a) uninstalled or b) I don't use.

How can I remove them from my menu.

Thank you in advanced

---

### Post by Olivier2371 on 2008-11-26
By any chance have you tried to use Add/Remove...

Applications->Add/Remove...

then select installed programs to see they are there.

---

### Post by KuroYoma on 2008-11-26
Yes I have, the menu won't let me right click either.  The programs that are in my way are "Windows XP" programs for managing my MP3 player and other random things.  I want them all out of my menu.  I have uninstalled all of them using wine. I have even uninstalled wine, don't use it anyways. But still they are in my menu in Applications-> Others and i can't get ride of them.

---

### Post by Olivier2371 on 2008-11-26
Try right clicking on the panel bar where the menus are,then, Edit Menus

---

### Post by KuroYoma on 2008-11-26
I get a small app with the Setting menus  some seperators and the i get


     NAME               COMMAND

Settings
   Settings Manager    xfce-setting-show
   --- seperator ---
   --- include ---     system
   --- seperator ---
Quit                   quit

So i can't actually see the menu just this so there is nothing to edit here

---

### Post by zvacet on 2008-11-26
If you can not remove it from main menu under others go to the **~/.local/share** and I believe you will find them there.

---

### Post by Olivier2371 on 2008-11-26
Could you post a screenshot please?

---

### Post by KuroYoma on 2008-11-26
zvacet:  thank you so much they were all there.  After deleting them my menu cleared right up immediatly.

---

### Post by zvacet on 2008-11-27
@ **Olivier2371**

In your **home folder>view>show hidden files** you will see .local and inside are subfolders and files.

---

