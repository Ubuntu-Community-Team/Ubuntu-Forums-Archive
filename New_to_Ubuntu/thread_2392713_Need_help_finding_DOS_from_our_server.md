---
title: "Need help finding DOS from our server"
date: 2018-05-24
forum: New to Ubuntu
---

### Post by kcurtis2 on 2018-05-24
Our ISP informed us that our mail server IP was sending DOS attacks. They shut down the IP. I installed the updates to our Ubuntu 16.04 and changed to a backup IP and it seems to be running fine now.

I assume what ever program was running the attack is still sitting on the server somewhere. May question is two part.

First how to identify what program on the server is causing the attack during the attack so I can find it and clear it if it comes back, and how would I be able to find it now that it is dormant before I have them restore the IP

---

### Post by kerry_s on 2018-05-24
check the /var/logs

the only sure way to remove is to nuke it, install clean. maybe look into hardening your setup.

---

### Post by SeijiSensei on 2018-05-24
What kind of attacks? Maybe your server was an open relay and being exploited by spammers.  You need to know specifically what they mean by a "DOS attack."

Meanwhile use the tools at mxtoolbox.com to evaluate the security of your mail service.

---

### Post by Habitual on 2018-05-25
[https://aw-snap.info](https://aw-snap.info)

---

