---
title: "No permission to write..."
date: 2008-04-25
forum: New to Ubuntu
---

### Post by Innernet on 2008-04-25
Good day!

I run pluggable hard drives, only one plugged at a time; each with ONLY ONE operative system, 6.10; 7.04; 7.10; WinXP; etc..., and an external USB hard drive with no operative system where only data is kept.

Removed the 7.10 in daily use, inserted the 7.04 hard drive to archive something into the USB data drive and got the message :

"You do not have permissions to write to this folder."

That never happened before, there is never been any other user on my compfuser, and could not find much about the subject.

Suggestions please ?

---

### Post by dark_harmonics on 2008-05-18
Are you trying to access the 7.04 drive from a hardy or gutsy install? Does the user you are logged in under have full permissions to that resource? You may need to run a chown command to give yourself ownership of the files.

---

