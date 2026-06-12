---
title: "Restoring program configuration and settings on another PC"
date: 2013-10-30
forum: New to Ubuntu
---

### Post by Wiking on 2013-10-30
If I want to restore setting and configurations for a program onto another PC what foloders would I need to copy and all associated files? bin, etc, dev, lib?

---

### Post by ian-weisser on 2013-10-30
Depends on the program.

Usually /etc/program or /home/user/.program or /home/user/.config/program
But some programs use /usr for default settings and /etc or /home for custom settings.
And (much) stranger ways exist.

It's a rich tapestry.

---

### Post by Wiking on 2013-10-30
So the best option would be to copy and paste every folder associated with the program then?

---

### Post by ian-weisser on 2013-10-31
Well, I think the best option is a bit of research to figure out which file(s) you really need.

Copying everything may work, or it may not. Depends on the program.

---

