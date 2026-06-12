---
title: "Can't empty trash"
date: 2014-08-22
forum: New to Ubuntu
---

### Post by dave131 on 2014-08-22
newbie here.  I followed some instructions on a net post to try to work with a driver, and ended up with a folder and it's contents owned by root but in my Downloads folder.  I found some information here on the forum about doing su nautilus so as to get temporary root access.  This let me move the folder to trash, however accessing trash in Nautilus gives an error.  Trying to just click on the trash icon and clicking Empty doesn't delete the folder from trash.  If I click on that folder in trash and select delete if says I don't have permissions.  So I found another net post about doing something we aren't supposed to (password to a "certain" user - don't think we're allowed to talk about that here) just so I could log on and try emptying the trash.  I have no way to enter a different userid at the login prompt, so I can't do it.  I went back and "reset" that account so I can't get back into it again (wanted to avoid any problems).

So.....I seem to be stuck with a folder in trash I can't delete!

Help??? ;)

---

### Post by dave131 on 2014-08-22
Ok, I got it.  Had to go to my trash (~/local.....) and chown recursive on every thing in the trash folder.  Just in case I also chgrp recursive on every thing in the trash folder as well.  Then I could select trash and empty it okay.

Whew!!

---

