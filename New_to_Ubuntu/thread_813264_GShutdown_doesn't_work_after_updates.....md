---
title: "GShutdown doesn't work after updates...."
date: 2008-05-30
forum: New to Ubuntu
---

### Post by jaydoc on 2008-05-30
The reason why I'm posting this is not bcoz I want to get it working again...!

Tht's a lost cause, I know. Bcoz i have asked this question a number of times on other Linux forums, and noone seems to have any viable solution to get it working again.

KShutdown..... Now there's a beauty. Could I use it on Ubuntu...? It being a KDE app and all that stuff...?

Anyway, the reason I need one of these is bcoz I need to conserve my allocated download limits so as to not incur high costs from my ISP.

To do tht I need to shutdown my system automatically at 08:00 ( 8 AM) everyday.....

**What is the terminal command i need to issue...? SPOON-FEED me plz...!** Bcoz, as I said, many tried giving me the syntax and all that stuff in general, but I just can't get the hang of it just now...! Newbie, plz put up with my ignorance....!

---

### Post by alexandremrj on 2008-06-09
I would recommend you take a look at this link, it talks about the same problem. You simply need to create a cron job (scheduler).

[http://ubuntuforums.org/showthread.php?t=210032](http://ubuntuforums.org/showthread.php?t=210032)

If you need any explanation just say so.

You can also put this in terminal every day that you want to shut down the PC

shutdown -hP 08:00

-h implies halt
-P it's poweroff

---

