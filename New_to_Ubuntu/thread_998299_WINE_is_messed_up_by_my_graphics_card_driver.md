---
title: "WINE is messed up by my graphics card driver"
date: 2008-11-30
forum: New to Ubuntu
---

### Post by Omegaomni on 2008-11-30
Ok...first things first...the attachment has my graphics card information (or at least as much as I think it may be...) so anyway continuing.....when my graphics card driver is turned on...WINE gets a distorted font problem...(you should see it in another attachment) and when said graphics driver is off everything is fine and dandy (check other attachment.) so.....getting right to the point...how do you think I can fix this?

---

### Post by Omegaomni on 2008-11-30
47....views....and no reply. :(

---

### Post by 4Orbs on 2008-11-30
Add this code to your .wine user.reg file to fix font smearing on the wine configuration gui.

```
[Software\\Wine\\X11 Driver] 1227050429
"ClientSideWithRender"="N"
"DXGrab"="Y"
"Managed"="Y"
```

The .wine folder is a hidden folder inside your Home folder. To find it, open your Home folder in the file manager and up at the top menu click on View and tick the option to Show Hidden Files. Then you can navigate to the .wine folder where you will find the user.reg file inside. You can then edit the file with gedit or other text editor, save and close. You might want to log out and back in before using wine again.

---

