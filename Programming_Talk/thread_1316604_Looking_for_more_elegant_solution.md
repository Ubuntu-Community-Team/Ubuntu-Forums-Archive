---
title: "Looking for more elegant solution"
date: 2009-11-06
forum: Programming Talk
---

### Post by OgreProgrammer on 2009-11-06
Here is my script, its ultra simple. xte is part of the xautomation package. You'll have to install that to test this out.

```

#!/bin/bash
xte "keydown Alt_L" "keydown F1" "usleep 1000" "keyup Alt_L" "keyup F1"

```It is stored in a file called startmenu.sh in my scripts folder in my /home.

It is then launched from the desktop. I have removed applications/places/system from my panel, which I intend to get rid of. 

The effect is that alt-f1 opens the main menu from the mouse cursor(which is over an launcher icon in this case). If there is an applications menu bar in the panel, it opens that. (You dont have to remove yours for the test).

I am looking for a solution that does not involve installing xte if possible. Any ideas would be appreciated. Is there a neater way to get this functionality? I guess what I am asking is this: what is the name of the application that opens the menu? That would be the easiest, but its been remarkably hard to find out.

---

