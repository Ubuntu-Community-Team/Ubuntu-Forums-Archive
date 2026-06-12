---
title: "create mail spool for user"
date: 2022-01-11
forum: New to Ubuntu
---

### Post by marcelosomething321 on 2022-01-11
I've seen many topics about use useradd command without creating a mail spool in /var/spool/mail/$USER.
How can I create a mail for a User that already exists on the system? 
Example: 
    root doesn't have a file in /var/spool/mail, so when an email is sent to root, it goes to /var/spool/mail/nobody;
    
I would like to create an email file for root. Does anyone knows how can I do it?

---

### Post by TheFu on 2022-01-11
I have never, ever, ever, needed to create anything under /var/spool/mail for users to have email access. Not once in 25+ yrs running personal and corporate email servers.
If you want root email to be sent somewhere else, use the /etc/aliases file. Don't forget to run newaliases after any changes.

---

