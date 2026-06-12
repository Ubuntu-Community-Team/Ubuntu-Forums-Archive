---
title: "When is &quot;Time of last access&quot; updated? (st_atime)"
date: 2009-09-30
forum: Programming Talk
---

### Post by Krijk on 2009-09-30
When programming I want to use the Time of last access. When testing though it seems that it isn't always updated.

The code below gives the st_atime of a new file in Unixtime:

```
>>> created new file
1254310331
posix.stat_result(st_mode=33188, st_ino=27525131L, st_dev=2069L, st_nlink=1, st_uid=1000, st_gid=1000, st_size=13L, 
st_atime=1254310331, st_mtime=1254309770, st_ctime=1254310331)
>>> opened file for the 1th time -> st_atime is modified
1254310352
posix.stat_result(st_mode=33188, st_ino=27525131L, st_dev=2069L, st_nlink=1, st_uid=1000, st_gid=1000, st_size=13L, 
st_atime=1254310352, st_mtime=1254309770, st_ctime=1254310331)
>>> opened file for the 2nd time --> st_atime is not modified!
1254310352
posix.stat_result(st_mode=33188, st_ino=27525131L, st_dev=2069L, st_nlink=1, st_uid=1000, st_gid=1000, st_size=13L, 
st_atime=1254310352, st_mtime=1254309770, st_ctime=1254310331)
```

When I open an existing file it is not modified. When I create a new file the st_atime is modified the 1th time it opens and afterwards it doesn't change.

Can anybody explain to me how this works?

---

### Post by Arndt on 2009-09-30
> **Krijk said:**
> When programming I want to use the Time of last access. When testing though it seems that it isn't always updated.

The code below gives the st_atime of a new file in Unixtime:

```
>>> created new file
1254310331
posix.stat_result(st_mode=33188, st_ino=27525131L, st_dev=2069L, st_nlink=1, st_uid=1000, st_gid=1000, st_size=13L, 
st_atime=1254310331, st_mtime=1254309770, st_ctime=1254310331)
>>> opened file for the 1th time -> st_atime is modified
1254310352
posix.stat_result(st_mode=33188, st_ino=27525131L, st_dev=2069L, st_nlink=1, st_uid=1000, st_gid=1000, st_size=13L, 
st_atime=1254310352, st_mtime=1254309770, st_ctime=1254310331)
>>> opened file for the 2nd time --> st_atime is not modified!
1254310352
posix.stat_result(st_mode=33188, st_ino=27525131L, st_dev=2069L, st_nlink=1, st_uid=1000, st_gid=1000, st_size=13L, 
st_atime=1254310352, st_mtime=1254309770, st_ctime=1254310331)
```

When I open an existing file it is not modified. When I create a new file the st_atime is modified the 1th time it opens and afterwards it doesn't change.

Can anybody explain to me how this works?

I see similar results here. I use the commands 'stat' and then 'touch' to modify a file and 'file' to read it. I suppose the file system may contain a cache for inode information. At previous times using Unix (Solaris, for example) when I've occasionally had reason to look at the access time, it worked the way I (and you) expected.

---

### Post by tom66 on 2009-09-30
The ext family of filesystems delay writes to the disk, so this information may not be updated. I don't know what filesystem you're using.

---

### Post by Krijk on 2009-09-30
> **tom66 said:**
> The ext family of filesystems delay writes to the disk, so this information may not be updated. I don't know what filesystem you're using.

I use ext3

I'm thinking about using the following, but am not sure if this will degrade my performance (or break things!)
```
To use /proc/sys/vm/drop_caches, just echo a number to it.

To free pagecache:

# echo 1 > /proc/sys/vm/drop_caches

To free dentries and inodes:

# echo 2 > /proc/sys/vm/drop_caches

To free pagecache, dentries and inodes:

echo 3 > /proc/sys/vm/drop_caches

As this is a non-destructive operation and dirty objects are not freeable, 
the user should run "sync" first! 

```

---

### Post by Arndt on 2009-09-30
> **Krijk said:**
> I use ext3

I'm thinking about using the following, but am not sure if this will degrade my performance (or break things!)
```
To use /proc/sys/vm/drop_caches, just echo a number to it.

To free pagecache:

# echo 1 > /proc/sys/vm/drop_caches

To free dentries and inodes:

# echo 2 > /proc/sys/vm/drop_caches

To free pagecache, dentries and inodes:

echo 3 > /proc/sys/vm/drop_caches

As this is a non-destructive operation and dirty objects are not freeable, 
the user should run "sync" first! 

```

These things are new to me, but I tried out the above commands, and they don't work for the purpose at hand - the access time is still not updated.

---

### Post by Krijk on 2009-09-30
> **Arndt said:**
> These things are new to me, but I tried out the above commands, and they don't work for the purpose at hand - the access time is still not updated.

I tried the same. No success either (although the echo 3 degraded performance for a few seconds :biggrin:). 

The attributes aren't reliable though. The create date and the inode are modified too when file is edited. The original becomes a backupfile (~) and the edited file gets a new inode.

Does anybody have suggestions how to log file access to get reliable data? In SELinux and Windows this is possible.

---

### Post by johnl on 2009-09-30
Check your /etc/fstab entry for the partition you are working with.  It's possible that it's mounted with the  'noatime' option.  

It's fairly common to disable access time updating for performance reasons, as it eliminates updating this info on disk every time a file is opened for read.

You might also have a partition mounted with the 'relatime' option which only updates access times if (I think this is correct) the previous access time is older than the current modified time.

---

### Post by Krijk on 2009-09-30
> **johnl said:**
> Check your /etc/fstab entry for the partition you are working with.  It's possible that it's mounted with the  'noatime' option.  

It's fairly common to disable access time updating for performance reasons, as it eliminates updating this info on disk every time a file is opened for read.

You might also have a partition mounted with the 'relatime' option which only updates access times if (I think this is correct) the previous access time is older than the current modified time.


noatime is not used. But relatime is! 
I'm going to look into it. I'll be back (as Arnold keeps saying)

---

### Post by Krijk on 2009-09-30
Changed mount-settings in fstab to norelatime and it's changing atime!

```
>>> 
1254321826
posix.stat_result(st_atime=1254321826, st_mtime=1254321599, st_ctime=1254321599)
>>> 
1254328298
posix.stat_result(st_atime=1254328298, st_mtime=1254321599, st_ctime=1254321599)
```

Thank's for all your suggestions.

---

### Post by Arndt on 2009-10-01
> **Krijk said:**
> Changed mount-settings in fstab to norelatime and it's changing atime!

```
>>> 
1254321826
posix.stat_result(st_atime=1254321826, st_mtime=1254321599, st_ctime=1254321599)
>>> 
1254328298
posix.stat_result(st_atime=1254328298, st_mtime=1254321599, st_ctime=1254321599)
```

Thank's for all your suggestions.

Googling for "relatime" shows that this is a quite new thing - added in 2007, and that it saves perhaps 5-10% time in disk traffic.

---

