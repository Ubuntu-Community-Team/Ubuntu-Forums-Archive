---
title: "How can I execute notification when already logged on."
date: 2010-02-03
forum: Programming Talk
---

### Post by lavinog on 2010-02-03
I am in the process of writing a notification script.

I am curious what would be the best way to have it execute.
It should execute once a week, for each user logged on.

I could just add it to the startup applications list for each user, but if a user never logs out, then it wont run the next week.
In this case I could just let it stay idle, but this seems wasteful. (although the overhead would be small)

I could use a cron job, but I don't know how to ensure that it runs for each user.  (I want user B to get the notification in case user A ignored it)

Also:  Is there a way to make sure that a user is not idle?  I recall something about gnome-screensaver used to keep track of this status.

---

