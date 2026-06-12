---
title: "root user session opened"
date: 2008-08-15
forum: New to Ubuntu
---

### Post by ub newb on 2008-08-15
Hi, 

I have read through some of the root user info on the boards here but please clarify something about it for me. 

What I have learned from my reading here? Stay out of root user unless you know what you are doing. 


Ok, so I have a question. I have noted another place on the forum that I had two computers get seriously compromised so I am very wary. I have looked through the logs as admin, and don't really understand yet much of what I am looking at but these entries confuse me. In the auth.log I keep seeing once an hour while everyone is asleep, that root user opens and closes sessions. Is this just something that runs in the background when no one is using the computer? 

the entries with xxxx are other users I would expect to see. 


Aug 14 22:17:01 MDdesktop CRON[6848]: pam_unix(cron:session): session opened for user root by (uid=0)
Aug 14 22:17:02 MDdesktop CRON[6848]: pam_unix(cron:session): session closed for user root
Aug 14 23:17:01 MDdesktop CRON[7698]: pam_unix(cron:session): session opened for user root by (uid=0)
Aug 14 23:17:01 MDdesktop CRON[7698]: pam_unix(cron:session): session closed for user root
Aug 15 00:17:01 MDdesktop CRON[8421]: pam_unix(cron:session): session opened for user root by (uid=0)
Aug 15 00:17:01 MDdesktop CRON[8421]: pam_unix(cron:session): session closed for user root
Aug 15 01:17:01 MDdesktop CRON[9144]: pam_unix(cron:session): session opened for user root by (uid=0)
Aug 15 01:17:01 MDdesktop CRON[9144]: pam_unix(cron:session): session closed for user root
Aug 15 02:17:01 MDdesktop CRON[9867]: pam_unix(cron:session): session opened for user root by (uid=0)
Aug 15 02:17:01 MDdesktop CRON[9867]: pam_unix(cron:session): session closed for user root
Aug 15 03:17:01 MDdesktop CRON[10590]: pam_unix(cron:session): session opened for user root by (uid=0)
Aug 15 03:17:01 MDdesktop CRON[10590]: pam_unix(cron:session): session closed for user root
Aug 15 04:17:01 MDdesktop CRON[11830]: pam_unix(cron:session): session opened for user root by (uid=0)
Aug 15 04:17:01 MDdesktop CRON[11830]: pam_unix(cron:session): session closed for user root
Aug 15 05:17:01 MDdesktop CRON[12707]: pam_unix(cron:session): session opened for user root by (uid=0)
Aug 15 05:17:01 MDdesktop CRON[12707]: pam_unix(cron:session): session closed for user root
Aug 15 05:49:49 MDdesktop gdm[5116]: pam_unix(gdm:session): session closed for user xxxx
Aug 15 05:50:13 MDdesktop gdm[5116]: pam_unix(gdm:session): session opened for user xxxxxxx by (uid=0)
Aug 15 05:50:14 MDdesktop gnome-keyring-daemon[13166]: Couldn't unlock login keyring with provided password
Aug 15 05:50:14 MDdesktop gnome-keyring-daemon[13166]: Failed to unlock login on startup


thanks

---

### Post by t0p on 2008-08-15
As far as the cron jobs go, it is normal for root sessions to open and close like this.  I think what's happening is: cron is popping up to see if there's anything it has to do, then popping off again.

---

