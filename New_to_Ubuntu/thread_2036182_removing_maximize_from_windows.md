---
title: "removing maximize from windows"
date: 2012-08-01
forum: New to Ubuntu
---

### Post by kabukiM0n0 on 2012-08-01
Hey guys
I'm trying to remove the maximize button from the windows and I can't quite figure out how it's done. 
I'm using gnome fallback. I've tried in gnome tweak, my unity, compiz (where I can't find the option) and dcomf (where its already changed too; :close, minimize. But doesn't do anything)

From the little knowledge I have .. I think I'm running on metacity - more than that I don't know...
I'm using the ambience-broken blue theme and Mirav2 for my windows. 

Thank you! :popcorn:

---

### Post by Linux_junkie on 2012-08-01
You need to run gconf-editor to remove the window buttons.

It may not be installed by default and will need to download it from repository.

press alt-F2  then type in gconf-editor to run it.  Cannot remember where in gconf-editor you need to edit but a simple search should  find the option.

---

### Post by stinkeye on 2012-08-01
Run this in terminal to open gconf at the appropriate section...
```
gconf-editor /apps/metacity/general/button_layout
```

---

### Post by kabukiM0n0 on 2012-08-01
Excellent! thank you!

---

