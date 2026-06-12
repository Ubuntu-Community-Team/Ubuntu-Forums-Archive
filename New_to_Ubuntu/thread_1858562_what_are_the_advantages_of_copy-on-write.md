---
title: "what are the advantages of copy-on-write ?"
date: 2011-10-12
forum: New to Ubuntu
---

### Post by Samik Ganguly on 2011-10-12
[FONT=Verdana][SIZE=2]As far as my knowledge goes, in copy-on-write file systems nothing is updated in place, updated data are written on new blocks and old data is deleted. So on average we are having twice as much disk access as we would have if we allocate new space for writing updated data.
 If we consider a file that grows over time by a small amount to a large size e.g. log files then every time we update it we have to copy the old content and the updated content to a new place. won't it slow down disk writes? 
And when the old contents get deleted the free space gets fragmented. So for a general user who doesn't need data-redundancy that much will it be helpful to have btrfs/zfs as file system?[/SIZE][/FONT]

---

