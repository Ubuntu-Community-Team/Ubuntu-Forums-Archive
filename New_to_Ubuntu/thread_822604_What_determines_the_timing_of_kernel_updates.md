---
title: "What determines the timing of kernel updates?"
date: 2008-06-08
forum: New to Ubuntu
---

### Post by bpl07 on 2008-06-08
What determines when the kernel is updated through Update Manager?  I'm currently using 2.6.24-18, but I see that the most recent linux kernel is 2.6.26 and the most recent stable kernel is 2.6.25.  Is it safe to try these kernels, or should I just stick to those released through the Update Manager?

I ask because supposedly mmap is fixed in the 2.6.26 kernel, which would enable me to open documents stored on an ntfs drive with office 2003 in wine.  Currently they open as read-only or not at all because of this mmap issue with ntfs drives.

---

### Post by bruce89 on 2008-06-08
If you really want to, you can compile the newer kernels yourself. However, some things might break.

---

### Post by OldTimeTech on 2008-06-08
And most probably the newest kernel hasn't been tested by Ubuntu's developers yet...so some things may not work that work with the kernel you now have.

---

### Post by kansasnoob on 2008-06-08
Something you might try for better read/write capability of ntfs partitions is adding ntfsprogs from synaptic. (I think it's in synaptic in Gutsy)

You can read more about ntfsprogs here:

[http://www.linux-ntfs.org/doku.php](http://www.linux-ntfs.org/doku.php)

---

### Post by bpl07 on 2008-06-08
So the timing is based on Ubuntu's developers testing and approving the kernel?

---

### Post by bruce89 on 2008-06-08
> **bpl07 said:**
> So the timing is based on Ubuntu's developers testing and approving the kernel?

They'll stick with the same minor revision, so 2.6.24's here to stay.

---

