---
title: "Unpack and burn"
date: 2007-10-21
forum: Programming Talk
---

### Post by maGot on 2007-10-21
Hi!

Is there a way to do a script or something that first can unrar (unpack) archivers and then burn the unpacked iso/img file to a dvd and then delete the iso/img file?

What would have been great!

/Best regards maGot! ):P

---

### Post by spin2cool on 2007-10-21
You want to look into creating a simple bash script, using the following commands:

unrar
cdrecord (for CDs)
growisofs (for DVDs)

Doing some searches will turn up more info on all of them.

---

