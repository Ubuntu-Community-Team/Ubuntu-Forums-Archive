---
title: "Which best way to use rsync to make a exactly mirror between two hard drivers over th"
date: 2022-10-23
forum: New to Ubuntu
---

### Post by netw844f on 2022-10-23
Hello,

I intend make a complete mirror between hard drives on same computer with ubuntu server. Which configuration should I use to make things security and correctly?


[LIST]
[*]sudo rsync -avz /home/user/origin/ /media/pen/destiny/
[*]sudo rsync -avz --delete-before /home/user/origin/ /media/pen/destiny/
[*]sudo rsync -avz --delete-after /home/user/origin/ /media/pen/destiny/
[*]sudo rsync -avz --progress --delete /home/user/origin/ /media/pen/destiny/
[/LIST]

Should I put slash "/" on end of directory path?
This is the list directory contents I have on my system regarding folders origin and destiny:

```

root@matt:/home/matt# ls -la disks/main_disks/
total 40
drwxrwxr-x   5 matt users  4096 Oct 19  2021 .
drwxrwxr-x   4 matt matt  4096 Aug 28  2019 ..
drwxrwxr-x 420 matt users 12288 Sep  4 21:04 disk2

root@matt:/home/matt# ls -la disks/mirror_disks/
total 16
drwxrwxr-x 4 matt matt 4096 May 19  2021 .
drwxrwxr-x 4 matt matt 4096 Aug 28  2019 ..
drwxrwxr-x 2 root  root  4096 May 19  2021 mirror_disk1

```

Thanks in advance

---

### Post by TheFu on 2022-10-23
```
$ sudo rsync -av --progress --delete /home/user/origin/ /media/pen/destiny/
```
is what I'd use.

Local storage sync doesn't get by compression. Over a network, it makes a huge difference.  Use with networking. Don't use with local disks.
The 'delete' option is require to ensure any extra files aren't left behind.
The trailing '/' matters most on the SOURCE, not so much on the target.

rsync is great at making file-based mirrors and there are many reasons to do that.
However, if you are trying to make a backup, use a real backup tool like rdiff-backup.  It is based on librsync and for a very similar command, we get extremely efficient versioning too for next to no extra storage (diff.gz files are used).  So, for typical documents and non-media files, there's very little extra storage needed to have multiple versions.
```
$ sudo rdiff-backup --exclude-special-files  /home/user/origin/    /media/pen/destiny/
```
The first run will create something effectively like an rsync mirror. The latest run always contains the latest mirror, with reverse differences storage in an rdiff-backup subdirectory at the top level.  The differences are tracked for not just the content, but for the user, group, ACLs and xattr changes over time.  That's a critical different from what all simple rsync scripts do even with versioning.  To restore from the most recent backup, cp, rsync, or 'rdiff-backup -r now' can be used. Your choice.  But we still have as many versions as we like (or our backup storage can hold).  I've been using rdiff-backup over a decade.  Typically, 90 days of daily backups uses 1.2x to 1.3x the source amount of storage.  Seems like a bargain to me.   Say you are backing up 20GB.  So, 90 days of daily, versioned, backups, would use about 26GB.  Versioned backups solve all sorts of issues that a simple mirror cannot address.  

If you want to up your game and have 2 systems, using a remote "pulled" backup solution (not pushed), and ensuring that the client system cannot access the backup storage on the remote system at all, will effectively prevent malware from encrypting your backup storage even if it does that to your clients.  rdiff-backup and rsync both support "pulled" backups. Those are a good idea.

---

### Post by netw844f on 2022-10-23
Thank you for your help. I will search more about rdiff-backup software. For now, I only know rsync and I only have experience with this software.
I intend only update the directory, because this folder already exist on destination but I want stay exactly equal of origin.

Do you recommend this command:

```
sudo rsync -av --del /path/to/source/ /path/to/destination/
```

Instead this command?

```
sudo rsync -av --delete /home/user/origin/ /media/pen/destiny/
```

Where:

--delete: delete extraneous files from dest dirs
--del: an alias for --delete-during

---

### Post by TheFu on 2022-10-23
Any of the options to delete is your preference.  I typically use --delete, but when the target file system is very full, sometimes that will fail and I need to use --delete-before.
I don't think it matters, but check the manpage for any relevant information.

---

### Post by cwmoser on 2022-10-25
I use **rsync** to backup my data partitions, and **dd** to backup my Linux OS partitions.

Will **rsync** also backup the Linux OS partition.

For **dd**, I do have to reset the UUID on the target to prevent conflict.

---

