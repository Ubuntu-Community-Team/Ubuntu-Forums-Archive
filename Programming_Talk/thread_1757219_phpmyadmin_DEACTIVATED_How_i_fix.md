---
title: "phpmyadmin DEACTIVATED How i fix ??"
date: 2011-05-13
forum: Programming Talk
---

### Post by thxbox on 2011-05-13
i have problem when install xampp and i can't use phpmyadmin because[FONT=monospace] mysql error [/FONT]#2002 **[SIZE=2]#2002 - The server is not responding (or the local MySQL server's socket is not correctly configured)[/SIZE]**

how i can fix it

thank you

[IMG]http://upic.me/i/6s/screenshot.png[/IMG]

---

### Post by LoneWolfJack on 2011-05-13
is mysql even running?

```

sudo /etc/init.d/mysql stop
sudo /etc/init.d/mysql start

```

---

