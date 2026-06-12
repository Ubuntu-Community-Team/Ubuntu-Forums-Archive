---
title: "fsck (I clearly don't know what I'm doing)"
date: 2008-08-11
forum: New to Ubuntu
---

### Post by karasuman on 2008-08-11
Someone mentioned running fsck to do a disk check in Ubuntu.  So, I opened up my handy little terminal, typed fsck, and got this:

```
beth@grumpy-laptop:~$ fsck
fsck 1.40.8 (13-Mar-2008)
fsck.ext3: Unable to resolve 'UUID=96f613e0-1371-4b81-860e-9bfa6ab5f983'

```

I read the manual page for fsck, but I still can't figure out what's going on.  Can anyone explain this to me?

---

### Post by pauper on 2008-08-11
[http://www.cyberciti.biz/faq/can-i-run-fsck-or-e2fsck-when-linux-file-system-is-mounted/](http://www.cyberciti.biz/faq/can-i-run-fsck-or-e2fsck-when-linux-file-system-is-mounted/)

---

### Post by OffAxis on 2008-08-11
It's generally a bad idea to run fsck on a mounted filesystem (which is why it fires up automatically after 30 or so reboots BEFORE mounting the drive)

You're getting that error because you're not running it as root; i.e. sudo fsck
UUID is the unique identifier of the hard drive (if I recall correctly).

The best thing to do is to fire up a liveCD and run it from there.

---

### Post by karasuman on 2008-08-11
Thanks...  As I thought, I had no idea what I was even trying to do.  :)  I'm still used to the way this sort of thing works in Windows.

---

