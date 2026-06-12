---
title: "Cannot log in to mySQL after 12.04 upgrade"
date: 2012-05-03
forum: New to Ubuntu
---

### Post by andperry on 2012-05-03
I've just upgraded from 11.10 to 12.04. The MySQL server is no longer accepting the previous/existing root username & password. (Fortunately I've got an image of my 11.10 system, so I can roll back temporarily, but that obviously doesn't solve the problem.)

Any ideas?

Thanks,

Andrew.

---

### Post by raja.genupula on 2012-05-03
[http://dev.mysql.com/doc/refman/5.0/en/resetting-permissions.html](http://dev.mysql.com/doc/refman/5.0/en/resetting-permissions.html)

---

### Post by andperry on 2012-05-04
Thanks for the reply. I still wasn't quite sure what to do so tried a different approach. Decided to try and uninstall/re-install MySQL as the database data was easy to restore. Entered the command:-

     *sudo apt-get remove mysql-server-5.1*

only to find that the package was no longer there anyway. MySQL had to be re-installed using:-

     *sudo apt-get install mysql-server*

which installs the server at version 5.5. On completion of the operation, my old database data was still intact!

Just one question, paricularly as I'm new to this process. If the upgrade took out the old MySQL server, should it have offered the new version as part of the process?

---

