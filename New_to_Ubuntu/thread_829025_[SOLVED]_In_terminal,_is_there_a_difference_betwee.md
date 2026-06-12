---
title: "[SOLVED] In terminal, is there a difference between find and locate?"
date: 2008-06-14
forum: New to Ubuntu
---

### Post by diablo75 on 2008-06-14
The find command...  The locate command.  What's different?

---

### Post by Joeb454 on 2008-06-14
I'm not sure exactly - but this happens with find ```
:~$ find topsecret
find: topsecret: No such file or directory
```

Whereas if I use locate, I get this ```
:~$ locate topsecret
/home/joe/topsecretstuff
/usr/share/cups/banners/topsecret
```

So that's why I use locate...actually I sometimes use ```
 locate <file> | less
``` That's if I think it'll return a lot of results

---

### Post by the_doc on 2008-06-14
locate uses a database and index method so is faster but the database has to be updated regularly and so can be unreliable if it isn't.  find does an actual directory hierarchy search each time and is slower but more relaible.

---

### Post by vishzilla on 2008-06-14
I think find searches in the current directory only. Locate brings more results

---

### Post by Joeb454 on 2008-06-14
You can update that database anytime you want, by running ```
updatedb
```From a terminal :)

---

### Post by the_doc on 2008-06-14
Locate will return results from all over the filesystem whereas find will only search the current dir unless specified otherwise.

It's also easier to update the database for locate with a cron job.

---

