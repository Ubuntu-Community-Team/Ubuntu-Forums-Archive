---
title: "RapidSVN problem"
date: 2008-01-20
forum: Programming Talk
---

### Post by Yoeri on 2008-01-20
I just installed rapidSVN.

When comitting, I get the following error:
Error: Error while performing action: Commit failed (details follow):
Can't create directory '/var/lib/svn/development/db/transactions/0-1.txn': Permission denied

I checked out a remote reporsitory withou any problems.

Any ideas?

---

### Post by animalmom on 2009-01-31
I run fc8 but I had the same problem.  Try starting the svnserve using sudo... that fixed it for me.

---

