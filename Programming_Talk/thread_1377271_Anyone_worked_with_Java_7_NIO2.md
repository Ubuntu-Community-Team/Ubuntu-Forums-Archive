---
title: "Anyone worked with Java 7 NIO2 ?"
date: 2010-01-10
forum: Programming Talk
---

### Post by kahumba on 2010-01-10
Hi,
The news is, among many new things, one can get info about partitions, their file system, size, but no obvious way to get the mount point info (how frustrating!).
That's done by java.nio.file.FileStore

The question is:
How do I get the mount point info/string from a FileStore?

Interestingly enough, FileStore contains the mount point info (but seems to have no interface to get it) because when doing a fileStore.toString() I get like:
> 
/media/sda3 (/dev/sda3)
There we have the "/media/sda3", but one can only get the "/dev/sda3" through fileStore.name() and no interface to get "/media/sda3".

ps: As a workaround to get the mount point I could parse the toString() info but that would be error prone.

---

