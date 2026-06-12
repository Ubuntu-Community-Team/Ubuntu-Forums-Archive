---
title: "remove linksys cit200"
date: 2012-06-01
forum: New to Ubuntu
---

### Post by westcoast01 on 2012-06-01
Hey folks, hoping someone can help me remove linksys cit200 from my machine. Played around trying to get it to work but no go and now I can not uninstall. Tried sudo apt-get remove ... uninstall ... purge ... but to no avail. Used Wine to install, it opens but can not locate skype and after reading and trying several ways finally gave up on it. Still studying Wine to see if that is how to remove it but have not found the answer yet. Thanks, West.

---

### Post by yeats on 2012-06-01
> **westcoast01 said:**
> Hey folks, hoping someone can help me remove linksys cit200 from my machine. Played around trying to get it to work but no go and now I can not uninstall. Tried sudo apt-get remove ... uninstall ... purge ... but to no avail. Used Wine to install, it opens but can not locate skype and after reading and trying several ways finally gave up on it. Still studying Wine to see if that is how to remove it but have not found the answer yet. Thanks, West.

If you installed something with wine, you have to remove it with wine.  There should be an Uninstall Wine Software menu item that would probably do what you're after.

---

### Post by westcoast01 on 2012-06-02
Mark this as solved. Finally figured it out, open a terminal and type  wine control   which opens the control panel for wine. Select add/remove and simply remove.

---

