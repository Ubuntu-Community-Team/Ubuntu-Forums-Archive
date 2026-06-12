---
title: "MS Powerpoint on WINE"
date: 2008-10-23
forum: New to Ubuntu
---

### Post by faraz_k86 on 2008-10-23
I want to use powerpoint on wine. but i get an error while installing it.

Openoffice presentation is good but it does not have text animations like if i want only one line to come at a time.

When i install powerpoint or msoffice from my CD, I get one of those windows has encountered a serious error and need to close error.....

help......

---

### Post by Crandom on 2008-10-23
Is this Office 2003 or 2007? Try looking at:

Office 2003: [http://appdb.winehq.org/objectManager.php?sClass=version&iId=3214](http://appdb.winehq.org/objectManager.php?sClass=version&iId=3214)
Office 2007: [http://appdb.winehq.org/objectManager.php?sClass=version&iId=4992](http://appdb.winehq.org/objectManager.php?sClass=version&iId=4992)

If it is Office 2003, Wine-Doors ([http://www.wine-doors.org/wordpress/?page_id=2](http://www.wine-doors.org/wordpress/?page_id=2) ) is a tool that automatically installs it for you using a script.

---

### Post by faraz_k86 on 2008-10-23
its office xp


---edit---


K so i can see from the winehq link that this is a common error that office xp crashes on installation, but 2003 does not.

so is there no hope for office xp?

or better still can i get the line per line animation in open office?

---

### Post by Crandom on 2008-10-23
Office 2002/XP then: [http://appdb.winehq.org/objectManager.php?sClass=version&iId=3514](http://appdb.winehq.org/objectManager.php?sClass=version&iId=3514)

EDIT: Try running this command and try it again:

sudo apt-get install cabextract

---

