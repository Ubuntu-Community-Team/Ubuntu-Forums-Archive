---
title: "cron.daily.lock could not be obtained"
date: 2008-09-29
forum: New to Ubuntu
---

### Post by mregister on 2008-09-29
Hello all,

I went to check log files this am and the user.log file has one line "aide-cron-daily: terminated because lock /var/run/aide/cron.daily.lock could not be obtained". I did a google search and did not find much. I am running Ubuntu Heron and it is setup with a LAMP box and I am also running ssh server. 

Any ideas? Thanks as always.

---

### Post by LowSky on 2008-09-29
found this -- [https://bugs.launchpad.net/ubuntu/+source/aide/+bug/114730](https://bugs.launchpad.net/ubuntu/+source/aide/+bug/114730), seems to be an issue with ubuntu not utilizing the folder /var/run/aide after the original installation. There is a fix posted as well, not sure if it works but worth a try, maybe.
[http://launchpadlibrarian.net/16194578/aide.debdiff](http://launchpadlibrarian.net/16194578/aide.debdiff)

---

### Post by mregister on 2008-09-29
I saw that. The problem is that I dont' have a /var/run/aide dir and this just started happening after running for over a month.

---

### Post by mregister on 2008-10-02
Ok the problem was with a bothced AIDE install. The cron job was trying to find a DB for the AIDE and there was not one so the job terminated with a fatal error. Removed AIDE and all is well.

---

