---
title: "Read-Only Problems."
date: 2011-10-03
forum: New to Ubuntu
---

### Post by missrachel on 2011-10-03
Hello.  I'm having a LOT of trouble deleting an ISO I mounted. When I try to access it with gksudo nautilus to change "owner" to myself, it says: "Sorry, couldn't change the owner of "ISO": Error setting owner: Read-only file system". So when I try to change "file access" to "read and write", it gives me no error but it doesn't change anything.

Also, my SD card is Read Only; won't change no matter what I do, and I tried to use an external drive a few weeks ago and got a mount problem.  I.m assuming these are all somehow linked.  I just don't know what to do.  Please help.  I'm very new to this.

---

### Post by seawolf167 on 2011-10-03
Did you unmount it before you attempted to delete it?

[https://help.ubuntu.com/community/Mount](https://help.ubuntu.com/community/Mount)
[https://help.ubuntu.com/community/Mount/USB](https://help.ubuntu.com/community/Mount/USB)
[https://help.ubuntu.com/community/MountIso](https://help.ubuntu.com/community/MountIso)

---

### Post by missrachel on 2011-10-03
I had tried that, but it wouldn't let me because I'm not root. Its okay now though, I rebooted and it was gone.  Stupid moment!

Do you know why my ISOs are automatically read-only?

---

### Post by seawolf167 on 2011-10-03
Think of an [iso]("http://en.wikipedia.org/wiki/ISO_image") as a disk image - just as you can't edit a cd after you write it, same with an iso file.

Yes the above statement is untrue; re-writable cds, editing iso files with something like *isomaster*, etc., but in general it works as an analogy.

If you have everything working, please mark this thread as Solved under Thread Tools.

---

