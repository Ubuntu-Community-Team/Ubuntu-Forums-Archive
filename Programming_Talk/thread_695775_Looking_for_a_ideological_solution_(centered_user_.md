---
title: "Looking for a ideological solution (centered user db, time restrictions, etc.)"
date: 2008-02-13
forum: Programming Talk
---

### Post by _Q_ on 2008-02-13
Looking for a good Linux solution for the local kiddies internet workshop. They have been terrorised for years with WinBlowz and it's time for a change.
But, it's not so easy, because there are certain terms that need to be met:

-> Centered user database (accessible via LAN) for access from various terminals

-> Daily time restriction

-> Different privilages for different users

In another words, user should be able to login at terminal A at any time, spend 30 minutes and leave. Later on, he comes to terminal B, and he then has only another 30 mins to spend (if the daily limit is 1 hour/user).

That's the basic problem i've been puzzled with so far. Back on windows, job was done by an app called "Watchdog".
I'm trying to think of a Linux solution, there are some mentiones of time restrictions on various forums by using PAM. But how to make it all tick while using a centered user database? :)

I'm open to any suggestions/ideas. Thnx.

---

### Post by pmasiar on 2008-02-13
edubuntu? It is based on Linux Terminal Server Project. Not sure about time limits, but those guys should knows.

---

### Post by M8M on 2008-06-13
This is the only reason I haven't ditched my Vista! If I could have more control as to when my kids can log on and be FORCED off when their time is up, and more control over what each user can and can't do, then I would DEFINITELY switch over to Ubuntu! Actually, I like your maximum daily time idea better. All of my 8 children do school work on the computer, but I can't be watching a timer all the time and some weeks they loose internet or email privilege, so I would like to have more control over such things. So, if this becomes available I WANT it!

---

### Post by _Q_ on 2008-10-22
I started to experiment with LDAP & PAM some time ago..
And managed to run a LDAP server successfully, but still having trouble with clients using the LDAP information for user authentication... :/

Since more than 6 months passed since the first post, maybe someone has some new ideas/suggestions? :)

---

