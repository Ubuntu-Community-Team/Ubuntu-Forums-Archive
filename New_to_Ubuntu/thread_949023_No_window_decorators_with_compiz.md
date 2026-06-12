---
title: "No window decorators with compiz"
date: 2008-10-15
forum: New to Ubuntu
---

### Post by NoSmokingBandit on 2008-10-15
Its been a while since i set up compiz. I just installed a minimal ubuntu install, grabbed compiz, emerald, ccsm, and fusion-icon and found a few good themes.
I run "compiz --replace" and my decorators go away. I ran "emerald --replace" and no go. I have the window decorators enabled in ccsm so idk what the deal is. Any ideas?

---

### Post by eternalnewbee on 2008-10-15
I had the same problem.
I reinstalled compiz, and had my window decorations back once more.
What you can try before doing that is disabling special effects in System > Preferences > Appearance and rebooting and enabling it again, and see if it works.
Good luck.

---

### Post by eternalnewbee on 2008-10-16
Any progress NoSmokingBandit?
Please let us know...

---

### Post by philinux on 2008-10-16
In CCSM click Effects category and tick the Window Decoration box. If it's ticked untick then tick again. Should sort it out.

---

### Post by NoSmokingBandit on 2008-10-16
I tried many a stupid thing to get this working (i like to tinker) and borked my system. Im working on finishing up a re-install and i'll see what happens then.
Thanks for the input guys, this time around i'll do thing the right way, lol.

---

### Post by Therion on 2008-10-16
This is usually caused by Emerald.  You can try a few things to resolve this...  You can install the [Compiz Switch](http://forlong.blogage.de/entries/pages/Compiz-Switch) to switch away from Emerald and back to your preferred window manager, or you can try using the Terminal:```
gtk-window-decorator --replace
``` Or you can stop Emerald from starting up automatically with Compiz, or you can uninstall Emerald altogether if you're not using it.

---

