---
title: "Searching files, folders or documents in Ubuntu 12.04?"
date: 2013-05-13
forum: New to Ubuntu
---

### Post by BSG Fan on 2013-05-13
I can not find that module or program more.
It was in Places - Search

Where is it now?
Any alternate program I can use to search documents and folders (any one)?

Thank you.

---

### Post by cmcanulty on 2013-05-13
install locate and mlocate, then in terminal type locate then any word in file name and you get instantaneous results. Can anyone explain why this is so fast and searching from a nautilus window is so slow?

---

### Post by schragge on 2013-05-13
> **cmcanulty said:**
> Can anyone explain why this is so fast and searching from a nautilus window is so slow? *locate* maintains a database of all files on the system that gets regularly updated per cron job. So it doesn't need to walk through all directories each time you make a query. The downside is, because the database usually gets updated once a day, *locate* will not find just created files or files that changed location since the last update.

---

### Post by BSG Fan on 2013-05-15
I just found in the net the answer to my question.

[http://www.youtube.com/watch?v=dh4UCP84uas](http://www.youtube.com/watch?v=dh4UCP84uas)

So I am closing my thread as solved.

---

