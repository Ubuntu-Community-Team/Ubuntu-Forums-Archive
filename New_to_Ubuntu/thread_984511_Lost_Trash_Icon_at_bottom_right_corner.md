---
title: "Lost Trash Icon at bottom right corner"
date: 2008-11-16
forum: New to Ubuntu
---

### Post by leclerc65 on 2008-11-16
My fingers are faster than my brain, I right click on the Trash Icon and DELETE it by mistake. Please help me to get it back. Thanks.:(

---

### Post by Zachx65 on 2008-11-16
> **leclerc65 said:**
> My fingers are faster than my brain, I right click on the Trash Icon and DELETE it by mistake. Please help me to get it back. Thanks.:(

On the bottom panel? Right click the panel and click 'Add to panel.'

---

### Post by leclerc65 on 2008-11-16
Many thanks from a newbie !

---

### Post by starcannon on 2008-11-16
If you would like a trash can on your desktop that is possible as well; though a little more involved.
To display the trash Icon on the desktop:
Alt+F2 and enter:
```

gconf-editor

```
Then open the following in the editor:
/apps/nautilus/[[COLOR=#D40000]****[/COLOR]]("http://ubuntuforums.org/member.php?u=103883")desktop

Now put a check mark in:
trash_icon_visible []

Look at some of the other icon options and checkmark any you would like, then close gconf-editor. Now you will see the icons you selected, displayed on your desktop.

GL and keep it fun

---

