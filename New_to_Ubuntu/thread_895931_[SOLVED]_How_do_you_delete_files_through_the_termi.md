---
title: "[SOLVED] How do you delete files through the terminal?"
date: 2008-08-20
forum: New to Ubuntu
---

### Post by phantomjoker on 2008-08-20
Hi, i need to delete files through the terminal

i don't have enough free memory to use  gksudo nautilus

and the files are protected - what is a command i can use?

- they must be permanently deleted since they are the files taking up so much memory.

---

### Post by drsaamah on 2008-08-20
use the command:
```
sudo rm FILE_NAME
```
If it gives you trouble, then use:
```
sudo rm -R FILE_NAME
```
BE EXTREMELY CAREFUL WITH THESE COMMANDS.  These actions are not reversible, so don't type anything in wrong and make sure you know exactly wht you're deleting.

---

