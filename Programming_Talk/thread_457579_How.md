---
title: "How?"
date: 2007-05-28
forum: Programming Talk
---

### Post by squinx22 on 2007-05-28
hi, gud day!

Anybody here who knows how to create a menu launcher using only shell commands?

I am now in a project that creates an installer.. I have to make a launcher in the menu for shortcut. What should I do? pls help me... thnx...

---

### Post by yabbadabbadont on 2007-05-28
Create one using the regular method, then look in the user's ~/.config directory  (or maybe it is ~/.local, I'm not sure and not using Gnome currently).  There should be a new entry there somewhere for the launcher that was added.  Examine the file and then figure out the correct "echo" commands you would need to duplicate it.  Isn't reverse engineering fun?  :D

---

