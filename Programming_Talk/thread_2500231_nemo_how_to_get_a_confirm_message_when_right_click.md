---
title: "nemo how to get a confirm message when right click wiping a file?"
date: 2024-08-26
forum: Programming Talk
---

### Post by ubto66 on 2024-08-26
```
[Nemo Action]
Name=wipe file
Name[en]=wipe file
Comment[en]=wipe file
Exec=/usr/bin/wipe -rf %F 
Icon-Name=gtk-dialog-warning
Selection=S
Extensions=any;
Quote=double
```

I added the action to nemo. Right clicking a file displays a wipe file option in the menu. And clicking wipe file deletes the file. I do not know how to verify if it wipes it correctly.
 How do you get nemo to display a confirm wiping message when you  click the nemo wipe file option? As it is, if you by mistake click wipe file the file in question gets  wiped. When it says Exec=/usr/bin/wipe -rf %F the f makes wipe discard  displaying a confirm message. By editing the nemo action file I tested  command Exec=/usr/bin/wipe -r %F. No confirm wipe message displays and  the file does not get wiped.
Thanks.

---

