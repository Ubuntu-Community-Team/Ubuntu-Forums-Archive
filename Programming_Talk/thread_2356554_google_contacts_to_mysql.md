---
title: "google contacts to mysql"
date: 2017-03-24
forum: Programming Talk
---

### Post by atux on 2017-03-24
hi. looking for a way to regularly download google contacts to mysql in my server. I have a few applications that ask mysql for Name and telephone of the contact. Mysql is the only communication between these apps.
The contacts will only need to get updated to the mysql from google contacts and not the other way around.
The communication to google contacts will be twice per day. One at 06:00 and the other at 18:00, through cron.
Any ideas on how can i achieve that please?

---

### Post by TheFu on 2017-03-24
Grab the contacts from google and store them into an ldif file. I wouldn't use mysql - I'd use ldap.  Then you can import the contacts directly into the ldap DB using the ldif file as input.  Probably a 5 line script.

Honestly, I wouldn't trust google contacts as my "system of record" - too many issues.  Plus some friends have lost all their contacts because they connected some smartphone app that screwed up.

---

