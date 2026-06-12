---
title: "Strange theme issue"
date: 2008-05-22
forum: New to Ubuntu
---

### Post by sports fan Matt on 2008-05-22
I have all these themes installed, problem is when I go to delete them in the window border, the "delete" button is greyed out..How Can i delete all the excess crap from my themes and reinstall them?  (I kind of want a clean slate with themes)

---

### Post by sayakb on 2008-05-22
Remove them from /usr/share/themes folder.

---

### Post by sports fan Matt on 2008-05-22
Can I do a gksudo to force them to get into my trash can? The option to move to trash is greyed out

---

### Post by forestpixie on 2008-05-22
I'd do it with gksudo nautilus - I'm still a bit wary of deleting some things with a terminal :)

---

### Post by Inxsible on 2008-05-22
```
sudo mv /usr/share/themes ~/.Trash
```Would go into your user trash.

---

### Post by nowshining on 2008-05-22
for folders u need to add -rf as options.
u can try placing a * after the / on the themes folder Example:

sudo mv -rf /usr/share/themes/* ~/.Trash


I also suggest creating aliases - look in my sig and go to my site ubuntu/kubuntu gatherings for more info.

---

