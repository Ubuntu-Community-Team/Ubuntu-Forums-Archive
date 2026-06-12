---
title: "Fatal error"
date: 2011-07-23
forum: Programming Talk
---

### Post by jackj on 2011-07-23
Running Ubuntu 10.04, Python.

Debgging my program, I got the following error:

'DB_RUNRECOVERY: Fatal error, run database recovery

I Googled it, and attempted a suggested fix, as many claimed it worked for them:

cd /var/lib/rpm
rm -f __db*
rpm --rebuilddb

Before I did this, there were four files in this folder, __db00, etc.

After I did it I now have no files.  Meaning the rebuild didn't work.

Again debugging my program and I get the same error.

I'm new to Ubuntu and in way over my head.  I would appreciate any help you have to offer.  I've never received an error such as this before.

---

### Post by Bachstelze on 2011-07-23
The commands you ran are for distributions that use the RPM package management system. This is not Ubuntu's case. How about you show us your program? We can't help you if we don't know what you are trying to do.

---

### Post by jackj on 2011-07-24
This error went away today, and I have no idea why.  Thank you, Ken, for being there when I was lost.  I couldn't get any responses on the Python forum.

If it pops up again, I'll re-post.

---

