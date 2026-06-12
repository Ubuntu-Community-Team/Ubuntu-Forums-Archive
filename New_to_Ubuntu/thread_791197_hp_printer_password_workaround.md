---
title: "hp printer password workaround"
date: 2008-05-11
forum: New to Ubuntu
---

### Post by Kevbo on 2008-05-11
Hope this helps.  I am still something of a newbie, but this worked for me.

I was unable to add my printer through an XP machine as the config tool kept asking for a password, but the XP machine had no password accounts.

On another thread, I found this, from nickrout:

<instead of running System|Admin|Printing open a terminal (or Alt-F2) and run:

gksudo system-config-printer

put your password into the dialog box and then configure the printer. Worked for me.>  Thanks nickrout!

Somehow it managed to get passed the password requirement and now logs in as guest on XP.

When it finished configuring, I was able to access my printer (hpDeskjet 3520) from Ubuntu through the XP machine but was unable to print. It would lock up. If this happens, go to Control Panel in XP > rightClick printer > selectProperties > on Ports tab uncheck "Enable bidirectional support".

Everything works! I am a happy guy.

Swimming in Ubuntu.
Kevbo

---

