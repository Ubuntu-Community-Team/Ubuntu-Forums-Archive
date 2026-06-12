---
title: "software center"
date: 2013-06-23
forum: New to Ubuntu
---

### Post by newbie2ubunt2 on 2013-06-23
i try and download software but I get a message untrusted files error then there are 2 buttons at bottom of window 1 says ok other says repair i push repair but nothing happens

---

### Post by fantab on 2013-06-24
How are you instaling the software?
If you are installing a .deb package (which is not available in Ubuntu Repositories) then you have to check the 'Permissions' by right clicking on the .deb file and opening 'Permissions'. Down there you will see 'Execute' 'Allow executing file as a program', select it by 'checking' the check box.

If you are installing from Ubuntu Repositories, say from 'Ubuntu Software Center' then from the 'Software Center' Menu:
Edit -> Software Sources -> (Software Updates) Ubuntu Software -> check 'Source Code' (enable it).

After enabling 'Source Code' you have to run the following in the Terminal [Ctrl+Alt+T]:
```
sudo apt-get update
```

---

