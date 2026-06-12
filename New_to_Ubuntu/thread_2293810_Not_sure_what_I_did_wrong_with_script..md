---
title: "Not sure what I did wrong with script."
date: 2015-09-07
forum: New to Ubuntu
---

### Post by jason_gibson2 on 2015-09-07
I wrote a backup function for my minecraft server. I have it backup to a location that is on google drive through insync. this is the function.

```
mc_backup() { # backs up minecraft server
	if pgrep -u "$USERNAME" -f "$SERVICE" > /dev/null ; then
		mc_saveoff
		tar -czf "$BACKUPPATH"/"$1"."$NOW".tar.gz "$MCSOURCE"/"$1"
		mc_saveon
		find "$BACKUPPATH" -type f -mtime +2 -exec rm {} \;
	fi
}

```

My problem is the find line. it wasn't working. I went to link my laptop to google drive today with insync again and all 15 gigs of my google drive space was full, hundreds of minecraft server backups ( i have the backup run every 15 minutes). Can someone point me to my error?

---

### Post by NathanRodriguez on 2015-09-07
You can try changing only the find line with different parameter for mtime without the rm (put a echo instead) until will setup one which correctly point your older backups.

---

### Post by jason_gibson2 on 2015-09-07
Further testing following your suggestion found my problem.

```
BACKUPPATH=/spinner/data/mcbackup/
```

instead of...

```
BACKUPPATH=/spinner/data/mcbackup
```

I had to end the path with a slash ( / ) and it works fine.

Now I just wonder how long it takes to free up my google drive space :/

---

