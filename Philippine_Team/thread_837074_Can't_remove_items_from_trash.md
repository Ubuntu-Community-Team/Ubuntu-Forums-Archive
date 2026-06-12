---
title: "Can't remove items from trash?"
date: 2008-06-22
forum: Philippine Team
---

### Post by adredz on 2008-06-22
it says "permission denied". anyone know how to navigate to the trash via terminal? don't know how :)

---

### Post by Oldsoldier2003 on 2008-06-22
> **adredz said:**
> it says "permission denied". anyone know how to navigate to the trash via terminal? don't know how :)
in hardy
```
cd ~/.local/share/Trash
```
in gutsy and earlier
```
cd ~/.Trash
```
If you get permission denied its probably because you don't have proper rights to delete the file. Use ```
sudo rm <filename>
```or ```
gksu nautilus
``` if you want to use the gui.

---

### Post by adredz on 2008-06-22
yeah i know all the sudo thing..
Thanks!:)

---

### Post by adredz on 2008-06-22
hey, when i typed "ls" inside the Trash directory, the files didn't match with the files i see when i open trash via file browser. maybe i am on the wrong place?

---

### Post by Oldsoldier2003 on 2008-06-22
> **adredz said:**
> hey, when i typed "ls" inside the Trash directory, the files didn't match with the files i see when i open trash via file browser. maybe i am on the wrong place?

if you are using hardy cd into the files folder.
```
cd ~/.local/share/Trash/files
```

---

### Post by adredz on 2008-06-22
yup, i have removed all of them already via terminal but when i open trash via file browser, there's still a lone directory present which i didn't find in the terminal. strange right?

---

### Post by adredz on 2008-06-22
will it do any harm if i will remove trash directory and make a new one again?

---

### Post by Oldsoldier2003 on 2008-06-22
> **adredz said:**
> yup, i have removed all of them already via terminal but when i open trash via file browser, there's still a lone directory present which i didn't find in the terminal. strange right?

did you do ls -a from the terminal? Without the -a you won't see hidden files or directories in your listing.

If you did thats pretty strange.... are the files from another partition?

---

### Post by adredz on 2008-06-22
mmm, this is really strange, i removed the trash directory and made a new one but to my surprise the bug folder is still there sitting like an ***hole...

---

### Post by Oldsoldier2003 on 2008-06-22
> **adredz said:**
> will it do any harm if i will remove trash directory and make a new one again?

It is not recommended to delete and recreate folders like the trash folder and the templates folder. Sometimes they don't work right after you do that.

---

### Post by adredz on 2008-06-22
i did ls -a...all i see are dots. three dots to be exact. what are they UFOs?:)
but they should not be present since i removed the Trash directory prior to that...

---

### Post by adredz on 2008-06-22
> It is not recommended to delete and recreate folders like the trash folder and the templates folder. Sometimes they don't work right after you do that.

now i'm messing up..:(

EDIT: it worked. deleting the Trash solved the problem. after making a new one, all is fine. the dots i mumbled lately, are normal IMO. i think, they are configuration files...
Thanks :)

---

### Post by lian1238 on 2008-09-26
> **adredz said:**
> i did ls -a...all i see are dots. three dots to be exact. what are they UFOs?:)


This is an old thread, but about the UFOs..
One dot means this directory; the one your in.
Two dots mean the parent directory of this directory; one folder up.
Just for knowledge. :)

---

