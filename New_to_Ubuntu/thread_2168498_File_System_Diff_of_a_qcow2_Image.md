---
title: "File System Diff of a qcow2 Image"
date: 2013-08-18
forum: New to Ubuntu
---

### Post by natalie2 on 2013-08-18
I need to create a script to compare a tampered with qcow2 image file system to its original.
I'm mounting each with nbd and I don't know of a good command or tool to use to find out which specific files have been read, touched, or modified.
The script will be written in python, if that makes a difference.
Thank you in advance.

---

### Post by TheFu on 2013-08-18
Doesn't **rsync** have a "test mode" where it just shows things that have changed and would be synced, if asked?  I thnk they call it a **dry-run**.

That should get you down to any likely changes for more review.  rsync is one of the greatest inventions of humanity.  Vaccines, creating fire, wheel, UNIX, and rsync.

---

### Post by natalie2 on 2013-08-18
Perfect! Thank you, TheFu.

---

