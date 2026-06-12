---
title: "[SOLVED] Naked Desktop Ubuntu 7.10"
date: 2008-05-03
forum: New to Ubuntu
---

### Post by ktechman on 2008-05-03
Is there any way to remove the hda and sda icons from the desktop without making them inaccessible unless rebooted, and make the change permanent. I upgraded to Hardy only to be stumped by twinview problems so I switched back to Gutsy. I liked the naked desktop look as the hda and sda icons didn't show up unless you needed access.

---

### Post by joselin on 2008-05-03
Open the configuration-editor (by typing gconf-editor) and look for apps/Nautilus/Desktop. Then unmark volumes visible.

Regards

---

### Post by ktechman on 2008-05-03
> **joselin said:**
> Open the configuration-editor (by typing gconf-editor) and look for apps/Nautilus/Desktop. Then unmark volumes visible.

Regards

Thank you for the help.  I love this actually getting a straight answer to a question without the endless google search.

Regards

---

