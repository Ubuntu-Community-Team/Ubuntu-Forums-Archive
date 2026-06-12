---
title: "Question about Postgres 8.2(hope this is the right place)"
date: 2007-08-18
forum: Programming Talk
---

### Post by Bentov on 2007-08-18
Hmmm, where to start, I have somehow screwed my postgres install, or I messed with a config file during one of my earlier attempts.  I can get postgres started with:

sudo /etc/inid/postgresql-8.2 start

When I try to create a db I get:

createdb: could not connect to database postgres: FATAL:  role "bentov" is not permitted to log in

so I then try:

createuser bentov

I'm asked if the new role should be a superuser, which I answer yes, then I get an error the same as before except createuser:.....

I've done a complete uninstall and reinstall, but no luck.  I've tried all the guides I can find.but no luck at all....running 7.04,

Thanks in advance for any assistance.

Bentov

---

### Post by glok_twen on 2007-08-19
there's another really good place to post for this - the nabble postgresql forum.

---

### Post by Bentov on 2007-08-19
Thanks for the reply, I will check it out.

Bentov

---

### Post by Bentov on 2007-08-19
Posted,,just have to wait and see what happens.  I'm at the point where it would just be eaiser to do a complete re-install of ubuntu just to get things back to the beginning.  :confused:

Bentov

---

