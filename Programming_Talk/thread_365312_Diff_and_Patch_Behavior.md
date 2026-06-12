---
title: "Diff and Patch Behavior"
date: 2007-02-19
forum: Programming Talk
---

### Post by shagymoe on 2007-02-19
I am trying to update directory A with changes that have been made to
a copy of directory A called directory B.  The changes include edits
and new files.  I'm trying to accomplish this via diff and patch.
( Yes, friends, I know the wondrous benefits of svn, but don't want to
use it in this case. :D  )

Anyway, I run the following diff command:

diff -Naur /home/shagymoe/A /home/shagymoe/B > /home/shagymoe/
b_to_a.diff

Then, I run the patch command:

patch -u -p0 --fuzz=3 < /home/shagymoe/b_to_a.diff >> /home/shagymoe/
b_to_a_patch.log

What I don't understand is that the patch command updates A with the
edits, but then tries to add the new files to B.  So, A is patched
with all of the edits and B is "patched" with the new files.  The
patch to B obviously fails because the files already exist and then it
creates a .rej file and logs the errors.

Ok, so here is the strange part.

If I do EXACTLY the same commands, but delete or rename B before
running patch, A is updated with BOTH the edits and the new files.
That makes no sense to me at all.  I've played with --unidirectional-
new-file and other things, but I just can't seem to make it do what I
want.

Any ideas?  Your help is greatly appreciated.

Shagymoe

---

