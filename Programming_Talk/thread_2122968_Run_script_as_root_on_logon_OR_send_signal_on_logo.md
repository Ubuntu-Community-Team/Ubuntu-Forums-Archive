---
title: "Run script as root on logon OR send signal on logon"
date: 2013-03-06
forum: Programming Talk
---

### Post by jazzpi on 2013-03-06
Hi,

I'm just teaching myself some Python and at the moment I want to program some sort of parental control thingy.
So far I managed to create a script that runs automatically on startup (/etc/rcS and /etc/init.d) and one that runs automatically on shutdown so I can monitor how long the computer is turned on.
But now I want to monitor which user is logged on when and for how long, so I've come up with two ideas:
[LIST=1]
[*]A script is run on logon - that needs to be run as root though so it can't be cancelled
[*]A signal is sent to the script on logon that is run on startup
[/LIST]
So now my only problem is to program one of these - any ideas?

---

### Post by SeijiSensei on 2013-03-06
Logins and logouts are logged automatically to /var/log/auth.log.

---

### Post by jazzpi on 2013-03-07
Thanks - That solves my problem :D
Didn't know about that...

---

