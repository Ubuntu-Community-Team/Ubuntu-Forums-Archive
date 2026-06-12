---
title: "Permissions and FTP"
date: 2016-01-05
forum: New to Ubuntu
---

### Post by wizkid2 on 2016-01-05
When I connect to my server (Ubuntu 14.04) via FTP, I only see directories where the group name matches my UserID's primary group.  
So I have directories similar to this:

drwxrws---  2  root op      4096 Jan  5 05:02 DirectoryA 
drwxrws---  2  root custsvc  4096 Nov  3 19:27 DirectoryB 
drwxrws---  7  root users      4096 Jan  5 05:02 DirectoryC 
drwxrws---  5  root admin      4096 Nov 1 05:03 DirectoryD 
drwxrws--- 11 root admin    12288 Dec  4 05:05 DirectoryE

I only see "DirectoryC" in the list, even though I'm a member of the groups op, custsvc, and admin. The primary group for my UserID is "users", and that's the only folder I have access to.

If I log in at the server (rather than via FTP), everything works as expected.  I have access to all of the above directories.

What am I missing?

---

