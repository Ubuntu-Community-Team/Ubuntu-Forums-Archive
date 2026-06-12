---
title: "MySQL  Grant Problem"
date: 2008-08-28
forum: Programming Talk
---

### Post by Griff on 2008-08-28
I'm automating the creation of mysql accounts through php.  I'd rather not involve the root user when creating these accounts so I created an 'employee' account to do this for me.  The main job of this acct is to grant access to tables under a specific database.  It has the global grant priviledge and all priviledges on the specific database and tables associated with that database however when I try to create a user acct I receive the following error : "You are not allowed to create a user with GRANT".  Seems obvious that I simply don't have grant priviledges but everything I look at tells me I do.  Any ideas?

Thanks,
Griff

---

