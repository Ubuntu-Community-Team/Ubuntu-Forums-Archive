---
title: "remove trash icon from desktop"
date: 2008-05-14
forum: New to Ubuntu
---

### Post by UnWarierMage224 on 2008-05-14
Hi folks, 

I think I put my trash icon on the desktop by dragging it down from the panels menu. I want to get rid of it because I have a trashcan icon in another panel. I can't highlight it and delete it because if I do I get some error "the specified location is not supported". I checked the desktop folder under my local folder (as sudo) and I checked the gconf-editor settings, of which the box to show the trash icon on the desktop is not checked. 

...

Thanks, 

-'Mage

---

### Post by RealPSL on 2008-05-14
You are definitely on the right track, however you do not want to start gconf-editor with sudo. Just start it by typing ALT+F2 then entering  ```
gconf-editor
``` in the editor.

Navigate to apps > nautilus > desktop > trash_icon_visible

Remove the check to remove the icon from the desktop.

---

### Post by UnWarierMage224 on 2008-05-14
Ah, wonderful! That worked! 

Thanks! 

-'Mage

---

