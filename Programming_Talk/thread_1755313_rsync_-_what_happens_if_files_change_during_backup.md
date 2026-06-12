---
title: "rsync - what happens if files change during backup?"
date: 2011-05-11
forum: Programming Talk
---

### Post by AbsolutIggy on 2011-05-11
I've searched google, but can't find the answer to this question..

What happens if the files of a backup source change while rsync is copying them? Change as in either new files appear, or existing ones change?

---

### Post by Grenage on 2011-05-11
If I recall correctly, rsync checks the directory contents upon initialisation, then generates a hash for those files.  The checksum will fail if a file has been modified during transfer, so it should automatically begin again for that file; if it fails a couple of times, then it will move on.  The data still gets copied, but only up to the point of the last transfer attempt.

Files created *after* the initialisation probably won't get copied until the next sync, but that's easy enough to test locally.

---

### Post by BkkBonanza on 2011-05-11
Yes, rsync will scan the files first and build a list. By default it only looks at file date and size though so if you want to actually check content you have to provide the option for that. 

A common way of dealing with changes during the copy is to do a "double rsync", that is, run the same command twice. The first one gets the bulk of changes and the second one runs much quicker since very little should have changed, and hence, since it runs quite quickly much less is likely to change during the second phase.

---

### Post by AbsolutIggy on 2011-05-11
Thanks for the answers guys.

I was pretty sure about the file list thing, but didn't expect the change check to be done at the beginning of the process only.. 

If I understand things correctly, that means that the file is copied if rsync at the beginning of the process sees that there have been changes. The actual changes which are copied depend on what is present when rsync reaches the actual file.. the changes which are not copied are those which occur after starting rsync, in those files which rsync had no intention of copying.

---

### Post by Grenage on 2011-05-11
> **AbsolutIggy said:**
> the changes which are not copied are those which occur after starting rsync, in those files which rsync had no intention of copying.

Bingo, that's right.

---

### Post by layr on 2012-03-30
What if the **--size-only** flag is being used? In that case, files are being compared based on their size instead of hashes. Does the flag change anything concerning mid-sync changes?

---

