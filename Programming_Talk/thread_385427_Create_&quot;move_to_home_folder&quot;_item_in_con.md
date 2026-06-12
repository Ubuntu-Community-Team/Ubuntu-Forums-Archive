---
title: "Create &quot;move to home folder&quot; item in context menu?"
date: 2007-03-15
forum: Programming Talk
---

### Post by loclarkey on 2007-03-15
Hi, this may be in the wrong section, but I have a feeling that the solution involves a bash script that I won't be able to come up with on my own.   How can you add a "Move item to home folder" item in the right-click context menu on the desktop?

Ubuntu Edgy 6.10
Gnome 2.16.1

---

### Post by Ramses de Norre on 2007-03-15
You can in the scripts menu, but getting it in the first menu will require you to hack on the source...
You can put this in ~/.gnome2/nautilus-scripts/ and set it executable.

```
#!/bin/bash
cd $NAUTILUS_SCRIPT_CURRENT_URI
for I in "$*"
do
    mv -i "$I" /home/`whoami`/
done

```

---

### Post by loclarkey on 2007-03-15
Thank you, Ramses.

---

### Post by Mr. C. on 2007-03-15
What the heck is that for loop doing, when it exits the first time?  Are you trying to get the first argument ?

Why not use $HOME instead of that /home/`whoami` ?

Hmmm...

MrC

---

### Post by sas on 2007-03-17
> **Mr. C. said:**
> What the heck is that for loop doing, when it exits the first time?  Are you trying to get the first argument ?


There might be more than one files selected. so it iterates through the selection.

---

### Post by Mr. C. on 2007-03-18
Not with that exit 0 there.

---

### Post by Ramses de Norre on 2007-03-18
Ow that exit line shouldn't be there, sorry.

---

### Post by Mr. C. on 2007-03-18
Right, exactly.

Now, since mv takes multiple arguments, why not ditch the for loop entirely and do:
```

  mv files .... directory
```

MrC

---

