---
title: "Latest file changes"
date: 2008-08-01
forum: New to Ubuntu
---

### Post by purplepaint on 2008-08-01
This might seem like a strange request, but is there any way (such as via a terminal command) to find a list of all the most recent file changes (such as new files and deleted ones) across the entire Filesystem in Ubuntu?  I don't mean recent documents, I mean all files that have been added to the hard drive in the space of, for example, a day.

---

### Post by NilsE on 2008-08-01
If you go into the places menu and select search for files in the options there is a modified less than or more than option but that won't help you with deleted files. Not sure about that other than looking in your trash folders.

---

### Post by purplepaint on 2008-08-01
> **NilsE said:**
> If you go into the places menu and select search for files in the options there is a modified less than or more than option but that won't help you with deleted files. Not sure about that other than looking in your trash folders.
Thanks!  That was all I needed!

---

### Post by rahmath on 2008-08-01
To find all files modified in the last 24 hours (last full day) "/" dir and its sub-directories:

$ sudo find / -mtime -1 -print

regarding the deleted --> no idea.

---

### Post by opscure on 2008-08-01
You could also do something like index the whole file system and then index again and use diff to see what changed.  For example (i use slocate for searching files):
```

#!/bin/sh
cd /
slocate * >/home/user/newlist
echo "new list created"
diff -EbB /home/user/newlist /home/user/oldlist >/home/user/changes.txt
mv /home/user/newlist /home/user/oldlist
gedit /home/user/changes.txt &

```

This will show you what was created and destroyed.  
You will need to update the slocate database and create the first index before running this script by simply doing a:
```
sudo slocate -u
slocate * >/home/user/oldlist
```

Oh, and be sure to change your path to your username (not user)

---

