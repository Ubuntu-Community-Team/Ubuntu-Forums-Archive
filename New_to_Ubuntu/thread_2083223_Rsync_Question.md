---
title: "Rsync Question"
date: 2012-11-11
forum: New to Ubuntu
---

### Post by chintz on 2012-11-11
I have a quick question about Rsync.

I have been using rsync as a backup utility on my FreeNAS by running DeltaCopy as the server on my Windows 7 machine and then having FreeNAS (running on FreeBSD) as the client running rsyncd tasks on a daily schedule to backup files.

I found that my Windows machine was doing all the CPU work.

I have since changed from FreeNAS to Ubuntu Server and wanted to make sure I have my facts right.

If I run Ubuntu as the server and Windows as the client, Ubuntu will do all the CPU work of checking all the files right?

Or does it not matter which way it is configured, it will still use equal amounts of CPU processes on each side.

Thanks in advance!

---

