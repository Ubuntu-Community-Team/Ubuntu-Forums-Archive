---
title: "script to backup website from FTP, versioning"
date: 2010-05-12
forum: Programming Talk
---

### Post by talz13 on 2010-05-12
Hi,

I need to make a script to backup the contents of a website via FTP to my home server.  There is only FTP access, no shell or rsync available.  Ideally, I would like to keep at least 30 days of backups (starting to edit my gf's business' website, and I don't want to screw anything up irreparably), and don't want to keep 30 separate, complete backups .

Can anybody help me with this?

---

### Post by hannaman on 2010-05-12
I think you want to put something like this in a script.
```
ftp -n *hostname* << EOF
user *username password*
*ftp commands here*
quit
EOF
```
This should work, but is not very secure (username and password sent in the clear) and not very elegant either.
sftp would most likely be a better choice, but I think sftp needs ssh as well.

---

