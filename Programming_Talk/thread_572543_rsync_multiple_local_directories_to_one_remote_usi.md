---
title: "rsync multiple local directories to one remote using one log file"
date: 2007-10-10
forum: Programming Talk
---

### Post by altonbr on 2007-10-10
Here's my script thus far:

```
#!/bin/sh

# %Y     year
# %m     month (01..12)
# %d     day of month (e.g, 01)
# %s     seconds since 1970-01-01 00:00:00 UTC

THEDATE=`date '+%Y%m%d-%s'` # 20071010-1192044000

# -a, --archive               archive mode; equals -rlptgoD (no -H,-A,-X)
# -v, --verbose               increase verbosity
# -r, --recursive             recurse into directories
# -z, --compress              compress file data during the transfer
#     --delete                delete extraneous files from dest dirs
#     --log-file=FILE         log what we're doing to the specified FILE
# -e, --rsh=COMMAND           specify the remote shell to use

rsync -avrz --delete --log-file=/home/admin/logs/rsync/rsync_log-$THEDATE.log --rsh="ssh -p 2222" '/var /etc' admin@00.000.000.000:/home/admin/rsync/server1/
```

It returns:
> 2007/10/10 15:08:39 [16208] building file list
2007/10/10 15:08:39 [16208] rsync: link_stat "/etc /var" failed: No such file or directory (2)
2007/10/10 15:08:39 [16208] done
2007/10/10 15:08:39 [16208] sent 33 bytes  received 20 bytes  3.93 bytes/sec
2007/10/10 15:08:39 [16208] total size is 0  speedup is 0.00
2007/10/10 15:08:39 [16208] rsync error: some files could not be transferred (code 23) at main.c(977) [sender=2.6.9]

Even though in the rsync man pages it says to use single quotes for multiple directories, it fails. So I can (and have) easily changed  '/var /etc' to /var but then that requires re-writing the line twice and having different log files. How can I send both directories with one log file?

---

### Post by wInddnIw on 2007-10-17
You can use 'localhost:' before the list of quoted dirs. Its working fine for me : 

rsync -avrz --delete --log-file=/home/admin/logs/rsync/rsync_log-$THEDATE.log --rsh="ssh -p  2222" localhost:'/var /etc' admin@00.000.000.000:/home/admin/rsync/server1/

My problem is that is seem to go through the network to do that. I don't know if it can't be speed up by using another syntax. Didn't found the answer yet.

wInd

---

