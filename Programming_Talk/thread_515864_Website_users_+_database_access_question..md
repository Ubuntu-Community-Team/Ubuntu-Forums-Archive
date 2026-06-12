---
title: "Website users + database access question."
date: 2007-08-02
forum: Programming Talk
---

### Post by Error1312 on 2007-08-02
Hi all.

I'm having a question about the use of mysql on websites. When there are multiple users that simultaniously need to read from the database or write to it, do I need a unique database account for every separate user? If so, then how must I connect to the database when the user is a guest and he/she has no account yet?

Or can I create one unique database account, i.e.: 'siteusers', that I can use for all database connections that are created, even when there are multiple users that need to access the database at the same time?

---

### Post by pmasiar on 2007-08-02
"user" of your database is website script generating response page. usually all scripts written by a programming team use same user, sometimes 2 users: one read-only for reports (which you can distribute more), and another for updating, which need be used with more care.

website users are completely separate concept. Maybe it is confusing, but thats how it is. Remember your data might be stored not in database - ie, every website user has her own subdirectoty with own files (named with some structure).

HTH

---

### Post by Error1312 on 2007-08-02
Ok, so one account can serve all users. 

Thanks for the quick answer.

---

