---
title: "Unison and Cron"
date: 2008-10-06
forum: New to Ubuntu
---

### Post by ckraimer on 2008-10-06
I'm trying to get a unison job to run in cron.  I already tried adding a script to cron.daily and that didn't work.  Now I'm back to using /etc/crontab (it has to be run by root so that all the directories can be backed up)
As you can see in the syslog, the job kicks off but there's no entry in the unison.log and it doesn't run. (roots aren't synced).


> Oct  6 09:54:01 ubu-d-xxxxxx /USR/SBIN/CRON[13651]: (root) CMD (/usr/bin/unison /mnt/filestore /mnt/mediastore/backups -fastcheck true -group -owner -force /mnt/filestore)


> # /etc/crontab: system-wide crontab
# Unlike any other crontab you don't have to run the `crontab'
# command to install the new version when you edit this file
# and files in /etc/cron.d. These files also have username fields,
# that none of the other crontabs do.

SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

# m h dom mon dow user	command
17 *	* * *	root    cd / && run-parts --report /etc/cron.hourly
30 6	* * *	root	test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily )
47 6	* * 7	root	test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.weekly )
52 6	1 * *	root	test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.monthly )
54 9	* * *	root	/usr/bin/unison /mnt/filestore /mnt/mediastore/backups -fastcheck true -group -owner -force /mnt/filestore
#


---

### Post by unutbu on 2008-10-06
Perhaps try changing
```

54 9 * * * root /usr/bin/unison /mnt/filestore /mnt/mediastore/backups -fastcheck true -group -owner -force /mnt/filestore

```
to 
```

54 9 * * * root /usr/bin/unison /mnt/filestore /mnt/mediastore/backups -fastcheck true -group -owner -force /mnt/filestore 2>/root/unison.out 1>&2

```
Then look in /root/unison.out to look for clues in the output.

---

### Post by ckraimer on 2008-10-06
Thank you.  I didn't realize the output was going to /root.  Once I did as you instructed the out file showed the errors Unison was throwing, as well as the location it was placing the files and I was able to fix it from there.  FINALLY my world is backed up automatically and I won't ever have to live through the horror of trying to restore deleted files from ext3 using [http://www.xs4all.nl/~carlo17/howto/undelete_ext3.html](http://www.xs4all.nl/~carlo17/howto/undelete_ext3.html) ever again!

---

