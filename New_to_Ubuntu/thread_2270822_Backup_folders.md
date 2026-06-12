---
title: "Backup folders"
date: 2015-03-25
forum: New to Ubuntu
---

### Post by kevingrant on 2015-03-25
Be gentle with me people as I am very new to this.

i have a server which I use for plex and as file storage holding photos, music etc.

What I want to do is backup some of these folder (music, photos) to a NAS which I have mounted, on a weekly basis.

i can't seem to find a simple software solution that's easy to use for a headless server.

any advise would be most gratefully appreciated.

Kevin

---

### Post by TheFu on 2015-03-25
"Easy" is dependent on your skill level.
For media, I use **rsync**. No need to mount anything usually - it has a network protocol and works over ssh by default.  Just setup ssh between the machines (which every network machine should probably already have anyway.  [https://rsync.samba.org/](https://rsync.samba.org/)
For personal files, system settings, and other things that aren't too big and might change, use a tool like rdiff-backup.  Versioning of these files is absolutely critical as is maintaining owner, groups and permissions - that means don't use NTFS - stay with a Linux-based file system on the backup storage. [http://www.kirya.net/articles/backups-using-rdiff-backup/](http://www.kirya.net/articles/backups-using-rdiff-backup/) has a nice primer.

"Easy"?  I think it is.

There are lots of other options. help.ubuntu.com and the ubuntu server guide will have pointers, plus there are at least 50 other questions here similar to yours. Search the forums a little.

Oh - and to automate anything on *nix - use cron.  [https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)   lots of good stuff there.

---

