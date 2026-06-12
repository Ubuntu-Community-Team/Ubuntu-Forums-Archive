---
title: "libmtp + Nautilus"
date: 2008-01-09
forum: Programming Talk
---

### Post by narehart on 2008-01-09
Does anybody have any idea on how to write a script that would call on libmtp to explore and transfer files using Nautilus?

---

### Post by MicahCarrick on 2008-05-22
I had trouble with it, but you could try mtpfs which will mount your MTP device allowing you to browse around. I was able to create files but it would often lose the connection and I would have to re-mount.

```

#install
sudo aptitude install mtpfs

# create dir
mkdir /media/SansaView

# mount
sudo mtpfs -o allow_other /media/SansaView

# unmount
sudo fusermount -u /media/SansaView
```

---

