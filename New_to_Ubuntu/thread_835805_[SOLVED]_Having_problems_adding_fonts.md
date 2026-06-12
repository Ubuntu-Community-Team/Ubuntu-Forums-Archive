---
title: "[SOLVED] Having problems adding fonts"
date: 2008-06-20
forum: New to Ubuntu
---

### Post by Dorkenfarber on 2008-06-20
I am trying to add new fonts. I was wandering throught the files and found the usr share fonts file, and I tried dragging and dropping the new font folder in and it says I dont have permission. I have already seen the official how to add fonts thing and there is no fonts on my system>preferences list. how do I get permission to drop fonts into usr share fonts?

---

### Post by ad_267 on 2008-06-20
/usr/share/fonts is for system wide fonts. If you want to drop something into there you can open up a file browser as root by pressing Alt-F2 and enter "gksudo nautilus"

If the fonts are only for your user the recommended way to install fonts is to put them in ~/.fonts which is a hidden directory in your home directory. If it isn't already there you can create it. Make sure it has the "." in front.

---

### Post by Dorkenfarber on 2008-06-21
thanks, I didn't know it was hidden. :)

---

