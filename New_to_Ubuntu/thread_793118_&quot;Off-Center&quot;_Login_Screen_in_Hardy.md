---
title: "&quot;Off-Center&quot; Login Screen in Hardy"
date: 2008-05-13
forum: New to Ubuntu
---

### Post by GregA on 2008-05-13
Since upgrading a vanilla hpA250N with geforce 4mx integrated graphics, I'm greeted with a very off-center display of the default graphics (user id window and logo, etc.).   It's almost like the size of the page is wrong, instead of 1280 x 1024, maybe it's like 1600 x 1200 or thereabouts.   How can I check this out and correct?   Thanks much.

BTW - after login, all the screens are reset back to the normal 1280 x 1024 - - so only the login screen is off-center.

---

### Post by bmac on 2008-05-13
Open file system/etc/X11/xorg.config
Section "Screen"
Change Virtual to 1024  768

Hope this helps...

---

### Post by GregA on 2008-05-13
Thanks bmac, I'll give that a try when I return home in a few hours (and I'll advise results).  I'm betting that's exactly the problem, as I had a botched attempt after install, of installing nVidia drivers (so me and xorg.conf are friends . . . ).

---

### Post by GregA on 2008-05-13
OK, thanks, that did it.  I had to change the virtual field from "1792 1344" to "1280 1024".  I wonder why the update didn't retain the settings from the prior xorg in Gutsy?   Oh well, it's back to normal now.

---

### Post by Inxsible on 2008-05-14
This had happened to me in my Xubuntu install in an old laptop as well. I guess it was probably because I chose a wrong screen size since during install it was attached to my bigger external monitor.

Must have been something silly like that for you as well.

---

