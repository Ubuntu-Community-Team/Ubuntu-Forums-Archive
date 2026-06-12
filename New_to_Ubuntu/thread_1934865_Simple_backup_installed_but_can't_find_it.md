---
title: "Simple backup installed but can't find it"
date: 2012-03-03
forum: New to Ubuntu
---

### Post by sarum on 2012-03-03
Hi, I backed up my 10.4; did a reinstall which mended what was wrong, and was supprised to find all was much as before.(bookmarks:most of my apps: and so on). But no Simple backup/restore. I've downloaded it and reloaded it - restarted twice but its not where it was; nor anywhere else.
Any ideas as to what I'm doing wrong please.

What was wrong in the first place was. After a change of ISP I couldn't get on the internet and I don't know enough to config things - reinstall seems a quick and easy choice.

Thanks.......sarum

---

### Post by Paqman on 2012-03-03
Try opening a terminal (Ctrl-T) and entering:
```
sbackup
```
and if it spits out errors copy and paste them in here.

---

### Post by sarum on 2012-03-03
No command 'sbackup' found, did you mean:
 Command 'sbackupd' from package 'sbackup' (universe)
 Command 'vbackup' from package 'vbackup' (universe)
 Command 'backup' from package 'openafs-client' (universe)
 Command 'nbackup' from package 'firebird2.1-classic' (universe)
 Command 'nbackup' from package 'firebird2.0-super' (universe)
 Command 'nbackup' from package 'firebird2.1-super' (universe)
 Command 'nbackup' from package 'firebird2.0-classic' (universe)
sbackup: command not found

Thanks for your reply, above is what I got..sarum

---

### Post by sarum on 2012-03-03
Thanks again I see what was wrong.

sbackup, and not simple backup, was what I wanted. Now installed. Cheers

---

