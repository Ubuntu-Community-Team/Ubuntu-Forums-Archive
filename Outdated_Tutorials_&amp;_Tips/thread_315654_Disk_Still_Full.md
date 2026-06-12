---
title: "Disk Still Full?"
date: 2006-12-09
forum: Outdated Tutorials &amp; Tips
---

### Post by Irony on 2006-12-09
Quite often people are somewhat non-plussed when they delete a bunch of stuff but find their disk is still as full as it was - this is because they delete stuff as root so it goes into the root bins. To get rid of this stuff type;

[PHP]gksudo nautilus[/PHP]

Press Ctrl+H to view hidden folders and then delete anything in;

[PHP]/root/.Trash
/.Trash-root
/root/.local/share/Trash[/PHP]

To do this deleting, select everything in the bins (Ctrl+A) and then hit the delete button on your keyboard.

Make sure you have the stuff highlighted in the bins and not somewhere else - you are in root so if you delete the wrong things you'll cause yourself a bunch of trouble.

---

