---
title: "Copy Thunderbird to Data partition"
date: 2017-10-03
forum: New to Ubuntu
---

### Post by oldfred on 2017-10-03
Moved to your own thread as not really related to thread you posted into.

No.

cd is change directory, cp is copy command but you probably need parameters to preserve ownership & permissions if copying to an ext4 formatted partition. At least -a parameter. And /mnt/data has to exist.
See also , q to exit
man cp

I prefer rsync and use several parameters. I do not have your exact command as I copy both Firefox & Thunderbird into one /mozilla folder in my /mnt/data partition or /mnt/data64 on 64 bit flash drive.

And then I back up to either my 32 bit or 64 bit flash drives with scripts. And I exclude a lot of cache or temporary files which I have in another file.
When I first try a new command with rsync I include -n parameter, so I can tell what it is doing. Or if I did not exclude all the temporary files.
# -n, --dry-run  perform a trial run with no changes made
See also:
man rsync

```
rsync -aruvP --exclude-from=mybackup_excludes64.lst  /media/fred/data64/mozilla/thunderbird/ /mnt/data/mozilla/thunderbird
rsync -aruvP --exclude-from=mybackup_excludes64.lst /media/fred/data64/mozilla/firefox/ /mnt/data/mozilla/firefox 

```

---

