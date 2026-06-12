---
title: "Sharing Entire Mounted Partition"
date: 2008-04-27
forum: New to Ubuntu
---

### Post by josef.sabl on 2008-04-27
Copying [this]("http://ubuntuforums.org/showthread.php?p=4759542") thread by zadkeo as it does not allow posting any more:

I am able to share my home folder using the new Nautilus way in Hardy, but when I try to share a FAT32 partition mounted as /fat_files it asks me if I want to set the permissions automatically, then fails to do so.

I also tried

sudo chmod 777 fat_files

It doesn't give me an error, but the fat_files folder is still set at 770. Can you not chmod a mounted partition like that?

What do I need to do to share /fat_files?

Note: I am having exactly the same problem as zadkeo in the original post.

---

### Post by PeterJS on 2008-04-27
FAT does not support UNIX/Linux file permissions, so it is given a fake set when it is mounted. So you would want to mount it with:
```

sudo mount -t vfat -o umask=000 /dev/something /some/place

```
or an fstab entry that looks like:
```

/dev/something     /some/place    vfat    defaults,umask=000      0    0

```

Edit/Disclaimer, I don't have a fat disk handy, there's probably a mistake in the above, and it's probably a stupid one.

---

