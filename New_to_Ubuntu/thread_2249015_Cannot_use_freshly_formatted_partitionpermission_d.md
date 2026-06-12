---
title: "Cannot use freshly formatted partition/permission denied."
date: 2014-10-18
forum: New to Ubuntu
---

### Post by kira-yamato-2008 on 2014-10-18
The partition is completely formatted, brand new, nothing on it. The problem is that I can't put files or folders on it. Even attempting to create a new folder causes a "permission denied" dialogue box. What do I do to fix this?

Edit: Wrong file system anyways switching to NTFS (What I wanted in the first place) fixed the issue.

---

### Post by haplorrhine on 2014-10-18
The *chmod* command changes permissions on files.[FONT=courier new]
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)[/FONT]
Alternatively, the *sudo* command would increase your privelages.

I've never dealt with partitions.

---

