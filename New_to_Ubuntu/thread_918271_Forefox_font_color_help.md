---
title: "Forefox font color help"
date: 2008-09-12
forum: New to Ubuntu
---

### Post by Raven_ on 2008-09-12
**I** installed a few new dark themes on Ubuntu and they looked pretty neat and awesome at first but then I realized that the lighter themes with the black text was kinder to my eyes. The problem is that when I changed my Ubuntu theme back to the standard *Human* theme the font color in forefox stayed white. Now I'm pretty sure I messed up something along the way.

I've tried to change the firefox theme a couple of times into themes in which I know have black text in the menus. Needless to say, it didn't solve my problem.

I figured it had something to do with my Ubuntu theme font color. However - in the menus, it's black but in firefox the font color is white. I'd like my black font color back in firefox but I'm not really sure how to get it back. Help?

---

### Post by Rolcol on 2008-09-12
Have you tried messing your with firefox preferences?  If you don't care about losing your addons or information (e.g. cookies, saved passwords, bookmarks, etc), you can delete (or rename) ~/.mozilla and have firefox startup like a "new" installation.

It's best to rename the folder rather than delete it so you still have your files.
```
mv ~/.mozilla ~/.mozilla.backup
```

---

### Post by cariboo on 2008-09-12
If you open Firefox ang go to Edit-->Preferences-->Content, you will see a font color button. Use it to change your font colours.

Jim

---

