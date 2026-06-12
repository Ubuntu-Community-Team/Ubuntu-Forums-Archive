---
title: "best backup strategy for media files?"
date: 2019-09-03
forum: New to Ubuntu
---

### Post by Tadaen_Sylvermane on 2019-09-03
Is there something other than just a direct copy or rsync for a boat load of media?

I'm currently at 1.4tb of media, with growth coming. The existing data never changes, just gets added to. What is the idea way to back this up?

---

### Post by TheFu on 2019-09-03
I use rsync. 
If you really want to ensure the data isn't corrupted, then you can use ZFS or create 10% par2 files for the media.  Assuming none of the files have spaces, 
```
#!/bin/sh
for filename in "$@"; do
   # Create a 10% recovery data with blocksize of 300KB
   nice par2 create -s307200 -r10 "$filename"
done
```

Both par2 and ZFS aren't needed. I would consider one or the other on the backup media sufficient.  I used par2 on optical media backups for years.  As the media failed, having the parity files made it possible to recover the media completely.

---

