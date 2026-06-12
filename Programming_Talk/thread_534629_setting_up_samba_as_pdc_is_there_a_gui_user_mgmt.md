---
title: "setting up samba as pdc is there a gui user mgmt ?"
date: 2007-08-25
forum: Programming Talk
---

### Post by pparvin on 2007-08-25
I am setting up ubuntu samba squid dg to be a proxy filter for external users to log into.  I anticipate 2-3000 users.  Is there a gui interface to add users already developed so you dont have to edit a file.  Can samba manage that many users?  I have googled and dont see a limit except for mem.  And finally, I dont need to share any other resources or alocate space for users, only want to filter for web content and send back out.  Any suggestions on how to set up database for different levels of filtering in the include stmts.

---

### Post by steve.horsley on 2007-08-25
The only GUI I know of is **gsambad** - it's worth giving a try, but back up your samba configuration first - apparently gsambad completely re-writes it. gsambad is in the Universe repository.

---

