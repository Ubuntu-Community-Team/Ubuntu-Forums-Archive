---
title: "Mysql, deleting data after some time"
date: 2007-08-11
forum: Programming Talk
---

### Post by orlox on 2007-08-11
Hi all.

Im developing a web site right now, and im looking for a way to make MYSQL delete a member from a table after some specified time. This is because I generate users that need to be authenticated by a confirmation, and if the confirmation is never done, then the member must be erased.

Also, Im looking for a way to change data after some time has passed (i.e. after 30 days from now, change the row state of a certain member in the DB to '1' unless I cancel this action before that time).

Is this possible:confused::confused::confused:

---

### Post by geek_Man on 2007-08-11
Please excuse my pitiful lack of instructions, but you might try writing a script (like Perl) that'll somehow manipulate the database and then make a cron job with the afore mentioned script. Again, sorry I couldn't help more...

---

### Post by Mirrorball on 2007-08-11
When you insert the member into the database, add the date of when the confirmation was sent. Periodically (for instance, every day) run a script that deletes the members that didn't do the confirmation.

---

