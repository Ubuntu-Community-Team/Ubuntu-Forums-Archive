---
title: "where is my Trash can?"
date: 2008-10-18
forum: New to Ubuntu
---

### Post by ellankavi on 2008-10-18
I can no longer seem to add the Trash can to the panel after it mysteriously disappeared. What is the command to delete the bin manually? And where is the Trash can actually located?

---

### Post by cairnzi on 2008-10-18
sudo rm -rfvI ~/.local/share/Trash/files/ this will delete all in the trash folder, try adding the bin again by going to the bar and right click then use add to panel.:)

---

### Post by owenll on 2008-10-18
> **ellankavi said:**
> I can no longer seem to add the Trash can to the panel after it mysteriously disappeared. What is the command to delete the bin manually? And where is the Trash can actually located?

If I understand your question correctly you can't seem to add it to the panel in the usual way? If this is so:

> Alt-F2 
Type > gconf-editor and press enter
In the Configuration Editor -> apps \ nautilus \ desktop
You can add it to your desktop and then drag it into a panel.

---

