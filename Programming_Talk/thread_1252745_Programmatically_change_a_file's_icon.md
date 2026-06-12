---
title: "Programmatically change a file's icon"
date: 2009-08-29
forum: Programming Talk
---

### Post by imbjr on 2009-08-29
A file's icon is determined by the appropriate XML file within /home/<user>/.nautilus/metafiles

For example, file:%2F%2F%2Fhome%2F<user>%2FDesktop.xml contains references to all the Desktop icons.

Now, I can go in there and change as I see fit, but the only way I can see of then making the changes visible is by restarting Nautilus:

nautilus -q
nautilus --no-default-window &

Which is ugly, since it will kill any nautilus session active.

Changing icons by the usual way of right-clicking the file and selecting a new image of course works, but how are they updating the display without messing with nautilus?

---

