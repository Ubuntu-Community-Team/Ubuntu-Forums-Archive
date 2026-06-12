---
title: "emacs jde install problem"
date: 2005-04-26
forum: Programming Talk
---

### Post by monkeyking on 2005-04-26
Hi has anyone tried the best lightweight ide for developing java programs.

Could anyone tell me how you installed it.
The apt-get for jde tells me that bsh, (that the beanshell), is a nonsuported dependecy,

I could install it myself, but does anyone know where the systemwide .emacs is hiding.

I did a locate and there is non.
I installed auctex, and a lot of other stuff and somehow it's all been added to my emacs. But no .emacs I don't get it.  :---) 

Thanks in advance
monkeyking

ps I crossposted this in the repossatory section also

---

### Post by rotorwash on 2005-04-27
[QUOTE=monkeyking]
...stuff deleted
Hi has anyone tried the best lightweight ide for developing java programs.

I could install it myself, but does anyone know where the systemwide .emacs is hiding.
[/QUOTE]
The site-wide emacs stuff is in /etc/emacs/site-start.d. You can also look in /usr/share/emacs/site-lisp/debian-startup.el for more information.

---

