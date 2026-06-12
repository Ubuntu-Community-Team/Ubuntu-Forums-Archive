---
title: "Hardy Heron: My Menus are gone!"
date: 2008-04-30
forum: New to Ubuntu
---

### Post by mikeserv on 2008-04-30
I just upgraded to Hardy Heron and I really like it.  I like the way it looks - especially since it kept nearly all of my settings.  Just one small problem: my menus are gone!  All of them, the right-click menus, status bar menus, any and all dropdowns that I used to have have now disappeared - but only with compiz running.  I'm pretty sure this has something to do with the fact that I had set-up some partially transparent menus in Gutsy - which may not be fully compatible.  And I.. hang on...

Ok.  I fixed it.  I killed Compiz (which isn't easy - apparently Hardy Heron has it rewired to automatically start Compiz over again if it crashes - I had to guess where the menu item for appearance would be in my invisible menu) and went into Advanced Desktop Settings and disabled my semi-transparent menus.  That's kind of a bummer - I liked them.

Other than that, it was an easy upgrade.  The whole process went very smoothly, and all of my fears were for nothing (I wasn't exactly running a clean install of Gutsy, either).

-Mike

---

### Post by Saint Angeles on 2008-04-30
try ```
sudo apt-get remove --purge compiz*
``` to remove all compiz stuff including config files. Then try ```
sudo apt-get autoclean
``` and ```
sudo apt-get autoremove
```. then reinstall compiz: ```
sudo apt-get install compiz*
```

i hope that works

---

### Post by mikeserv on 2008-04-30
No, none of that is necessary.  As it turns out, the old version of Advanced Desktop Settings that I had rated transparency on a scale of thousands, while the new version rates it in percent: 1-100.

Anyway, my setting was 12000 or something, which is obviously invisible.  So I reopened my updated ADS and set it to 85% opaque or something.  

Problem Solved.

-Mike

P.S.  How do I mark a thread "[Solved]"?

---

