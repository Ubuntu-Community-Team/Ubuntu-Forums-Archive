---
title: "external HD"
date: 2012-12-13
forum: New to Ubuntu
---

### Post by Robert1305 on 2012-12-13
When I start Ubuntu I get the message...."Maxtor HD not ready or not present, Wait, skip, or load manually.

The external HD is not connected to this PC, how do I get rid of this annoying start-up interruption.:mad:

Regards Bob

---

### Post by JRV on 2012-12-13
You need to remove the disk from your /etc/fstab file.

Make a backup of the file.

Then edit the file with the command:
```

gksudo gedit /etc/fstab

```

If you don't know which line to remove post a copy of the file here and I (or someone else) will help.

Be careful, a mistake editing this file can make your system unbootable.

---

