---
title: "Disk Space is full and can't find what is using it."
date: 2022-11-08
forum: New to Ubuntu
---

### Post by christiaanlouw on 2022-11-08
Good day. 

I am fairly new to Linux and I have a problem where my disk space fills up but after hours of trying different commands and apps, I cant find what is using up the space. 

I managed to delete some logs and timeshift backups to get the pc going again but there is still over 300GB missing and I cant find what is using it.

---

### Post by TheFu on 2022-11-08
There are lots of ways to find which files are using storage. A number of threads here have covered that. Did you search for those long answer here already?  

Generally, I'd start with 2 commands:
```
df -hT -x squashfs -x tmpfs -x devtmpfs
df -hi -x squashfs -x tmpfs -x devtmpfs
```
Ensure neither are close to 100% used.  The 2nd command looks at inodes. The first looks at blocks. Either can become full. About 99.9% of the time, the inodes will be fine, but that tiny risk is real. I've run out of inodes on a file system about 3 times in my life, so it can happen.

When searching the forums for similar questions, look for my username and 'du -sh /*'  There may or may not be a sudo before it. That should find at least 20  threads.

There's also 'ncdu', but I find it slow and cumbersome compared to 
```
$ du -sh /* | sort -h
```
then I walk down the fullest directories that have temporary files.  So, I wouldn't worry about /usr, but I would worry about /var and /boot and /home. Walk down each directory where the largest files are and use the sort to pay attention to which things are using the most storage. They will be at the bottom of the list each time the command is run. Obviously, you'll need to chdir/cd into the directory and not use /*, as the location for du to look.  Basic stuff.  Again, sudo might be needed for /var, since those files will have limited access to normal users.

---

### Post by Impavidus on 2022-11-08
There appears to be a bit much in your /var (normally maybe 2GB, but some logs get vacuumed automatically to use a reasonable fraction of the filesystem, which is quite big in your case) and in /root (that's root's home directory, normally almost empty, with just some config files and terminal history). But that's nowhere near the size of the filesystem you report.

Maybe some files are hidden underneath a mountpoint. If that happens, tools like du can no longer see them. Maybe you tried to copy a large amount of files to one of your network drives without realising it hadn't been mounted, filling up the root partition. Now it is mounted and hiding the big files underneath. Try unmounting your network drives and see if there's anything hiding under those mountpoints.

---

### Post by TheFu on 2022-11-08
> **Impavidus said:**
> There appears to be a bit much in your /var (normally maybe 2GB, but some logs get vacuumed automatically to use a reasonable fraction of the filesystem, which is quite big in your case) and in /root (that's root's home directory, normally almost empty, with just some config files and terminal history). But that's nowhere near the size of the filesystem you report.

Maybe some files are hidden underneath a mountpoint. If that happens, tools like du can no longer see them. Maybe you tried to copy a large amount of files to one of your network drives without realising it hadn't been mounted, filling up the root partition. Now it is mounted and hiding the big files underneath. Try unmounting your network drives and see if there's anything hiding under those mountpoints.

Mounting extra storage under a HOME directory seems to always cause hassles. This is one, but there are at least 20 others. Best to avoid it by mounting storage elsewhere, then using symbolic links from $HOME to make getting to those other locations just as easy.  Symlinks can point to directories or files. In this situation, it would be a directory that was mounted, perhaps to /media/ somewhere.

It would be really helpful to see 'sudo du -sh /var/*  |sort -h' output.  Just need the last 10 lines at the bottom, perhaps less.

---

### Post by deadflowr on 2022-11-08
> There appears to be a bit much in your /var 
Both snaps and flatpaks eat space in /var/lib.
it's where the actual disk space is used for those.
/snap directory is just a mountpoint location where the squashfses are mounted.

Typically the output that is seen there is accurate.
the -x option in du command skips the actual usage since those are technically a different file system.
So ```
du -shx /snap
```will look different from
```
du -sh /snap
```
But in general, that doesn't matter because /snap holds no actual disk space.

---

