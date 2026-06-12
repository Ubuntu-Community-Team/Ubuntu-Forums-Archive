---
title: "Why won't my script work?"
date: 2008-06-10
forum: New to Ubuntu
---

### Post by Twizzle on 2008-06-10
I am trying to write my first script to run a backup / sync procedure when the computer starts up.

This is what I have so far:

```
#!/bin/bash
unset PATH

#Check and sync Music
rsync --archive --fuzzy --delete-after ~/Music --progress --stats --human-readable /home/john/SERVER/Data/

#Check and sync Pictures
rsync --archive --fuzzy --delete-after ~/Pictures --progress --stats --human-readable /home/john/SERVER/Data/Pictures
```

I have saved it as 'backup.sh'. I have also chmod 755 it.

If I run it, though, I get:

```
john@office:~$ '/home/john/backup_1.sh' 
/home/john/backup.sh: line 5: rsync: No such file or directory
/home/john/backup.sh: line 8: rsync: No such file or directory

```

which is strange as I understand that to mean it can't find 'rsync'.

If I run just the rsync line its self in the terminal, it works.

It is my first foray into the script world, so I am sure I have done something stupid!

---

### Post by Twizzle on 2008-06-10
As I said.... something stupid!

I just realised I had unset PATH at the top!

It seems to work now...

---

### Post by |{urse on 2008-06-10
remove unset path.

oh lol didn't see your next post ^^

---

