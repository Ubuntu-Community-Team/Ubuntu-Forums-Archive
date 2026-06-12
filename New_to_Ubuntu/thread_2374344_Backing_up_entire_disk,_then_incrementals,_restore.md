---
title: "Backing up entire disk, then incrementals, restore if needed"
date: 2017-10-14
forum: New to Ubuntu
---

### Post by sterator on 2017-10-14
I'm migrating from OS X, so I'm used to Time Machine, but I've also used rsync to handle backups manually by typing the commands into a terminal. I would like to backup my entire Ubuntu install, apps, files, system and all, then do incremental backups at User-selectable intervals.

"Backups" is on my system, but it fails to actually back up. Throws this error:  

```
"Failed to execute child process “duplicity” (No such file or directory)"
```

Can someone point me to the road to successful backups? Am I missing a piece, or do I need to choose something other than "Backups?"

Thank you!

---

### Post by HermanAB on 2017-10-15
Well, the thing is that installing Linux/BSD is very easy and when you had a HDD crash, you would like to use the latest and greatest Linux version and not an old tired version from a backup.

Therefore, the general philosophy with Linux/BSD backups is different from other systems.  Backup your data.  Forget about backing up the whole darn system, since that is a waste of time and media.

---

### Post by gordintoronto on 2017-10-15
Ubuntu includes rsync, so you could use it.

---

### Post by ian-weisser on 2017-10-15
> **sterator said:**
> "Backups" is on my system, but it fails to actually back up. Throws this error: 

That means the icon for duplicity is installed, but seemingly not the actual application.
Reinstall duplicity (sudo apt install --reinstall duplicity) and try again.

---

