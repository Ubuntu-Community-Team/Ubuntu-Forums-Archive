---
title: "transfering files from a cd, locks on files"
date: 2008-12-01
forum: New to Ubuntu
---

### Post by orwellus on 2008-12-01
I recently did a fresh install of ubuntu 8.10. I have it pretty much configured the way I want. But, I am having a problem. When I try to transfer or copy/paste files or folders from a cd onto ubuntu, ubuntu puts a lock on the folder or file. I can remove the lock but right clicking and changing the permisson to I think read and write. Is there anyway to fix this so when I transfer a file there is no lock? Seems like in Ubuntu Gutsy this was not a problem. Another weird thing is if I transfer a file or folder from my flash drive, there is no problem. Help would be appreciated.

---

### Post by The Cog on 2008-12-01
I think the CD file system is implicitly read-only, so that any file you copy off a CD is copied with read-only properties. I don't know of a way round this. Files stored inside tar files keep their original permissions so it may be worth using tar archives on the CD (if appropriate).

---

