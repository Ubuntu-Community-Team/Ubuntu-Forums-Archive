---
title: "File Permissions"
date: 2008-06-15
forum: New to Ubuntu
---

### Post by Mythrandil on 2008-06-15
I run Ubuntu in dual boot with Vista and have a 60gb fat32 "share" partition for docs, music and videos.

A problem I have come accross is that applications try to write permissions meta data to files they are saving, which of course they can't on fat32 as it doesn't support it.

Is there any way to prevent them adding the permissions info and just saving it as a simple file? 

Examples of such programs I've encountered this in are anjuta and unzipping tar.gz files.

---

### Post by vajorie on 2008-06-15
you don't really need to do anything. they should be able to save / edit the files just fine even though they may spit out errors (except rsync and the like probably)

---

### Post by scorp123 on 2008-06-15
> **Mythrandil said:**
>  A problem I have come accross is that applications try to write permissions meta data to files they are saving, which of course they can't on fat32 as it doesn't support it.  As for metadata ... That's 'normal'. Linux filesystems such as ReiserFS and EXT3 may have features such as UNIX-style file permissions that are not present on FAT32. So if you write a file with such permissions to a FAT32 permission that the system will complain that it can't write the file 1:1 with all the permissions. That's normal. You shouldn't lose any of the content though, e.g. you shouldn't get corrupted MP3 or video files or anything like that.

---

