---
title: "remapping keys"
date: 2011-12-30
forum: New to Ubuntu
---

### Post by degarb on 2011-12-30
On this notebook, kids ruined several keys.  I remapped the essential ruined keys to lesser used keys.  Now,I wish to remove the printscreen key that I accidentally keep tapping every 3 minutes and remap it to backspace, but after 1 hour and 45 minutes of googling, I am giving up, nearly.  I don't remember how I did this, before.

My best guess is I used xev .  This crude and weird tool kinda tells  the key code or serial 22 for print screen key....Then I use xmodmap , but nothing i type works.  Then /home/.xinitrc  reads xmodmap .Xmodmap  which makes no sense, but something has to be done

---

### Post by degarb on 2011-12-30
After about 2 hours, I discovered that xmodmap was designed to torture and dissuade new users from the OS.  It is far easier to just gedit the .xmodmap file.  xev is needed, or at least useful.  The name xev should be changed to change to something more memorable, like keycode.  That, would be too easy.  It would be genius just to merge the two tools; but would make things too easy.

Also, if the xmodmap file exist then load, would be too easy.  I fortunately didn't need to alter my script to load the xmodmap.

---

