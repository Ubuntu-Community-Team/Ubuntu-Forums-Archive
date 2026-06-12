---
title: "[SOLVED] problem with Mac4Lin"
date: 2008-11-08
forum: New to Ubuntu
---

### Post by luckydeveloper on 2008-11-08
hi,

i recently installed Mac4Lin package and it gave me some Mac look to my system. But today, i actually didn;t want that look and tried to change it to human theme. 

I changed the look to human theme but in window title bar, the minimize,maximise and close buttons are still in the left side of the title bar(like it was before in MacOS theme).
 
note: for installing Mac4Lin, in the package tar file, there was a script file to install Mac4Lin... i guess this package could have made this thing... how can i uninstall Mac4Lin.. may be that could solve the problem..

if not, what may be the problem... please help

---

### Post by earthpigg on 2008-11-08
its somewhere in configuration editor (gconf-editor from terminal).... im looking now cuz i cant remember :)

---

### Post by earthpigg on 2008-11-08
found it.

```
gconf-editor
```

apps->metacity->general-> make button_layout read:

```
menu:minimize,maximize,close
```

---

### Post by thunk77 on 2008-11-08
Alright.

Hit Alt+F2 and type gconf-editor.

Then navigate to apps -> metacity -> general

In the button_layout entry change the value to: menu:minimize,maximize,close

and you're ready! :D

---

### Post by luckydeveloper on 2008-11-08
thanks... i did it as you people said, now its fine.. thanks again

---

