---
title: "command won't run"
date: 2013-07-18
forum: New to Ubuntu
---

### Post by emerson1979 on 2013-07-18
Hello Everyone                I ran the following command. I took the command from a Ubuntu book. Why does it say "permission denied"?  root@dan-MS-7369:/home/dan/Music# chmod -R 744 /home chmod: cannot access `/home/dan/.gvfs': Permission denied  Thanks

---

### Post by steeldriver on 2013-07-18
The command ran, it just skipped the directory where it didn't have permission to do what you asked it to do (.gvfs is a mount-point for user-mounted remote filesystems, and only the owner has permission to change it - root can of course *become *the owner)

---

