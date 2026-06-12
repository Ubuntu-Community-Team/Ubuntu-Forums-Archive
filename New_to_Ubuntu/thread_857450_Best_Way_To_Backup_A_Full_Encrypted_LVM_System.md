---
title: "Best Way To Backup A Full Encrypted LVM System?"
date: 2008-07-12
forum: New to Ubuntu
---

### Post by TSS on 2008-07-12
I've just recently installed Ubuntu 8.04 using the alternate installer.  I've set up a small boot partition and one huge encrypted LVM partition.  The LVM partition is divided up into root, home, and swap logical volumes.  I'm looking for a secure way to back up my data.  I have an extra box that I can use if I need to.  Thoughts?

TSS

---

### Post by gate on 2008-07-12
Well,
  I have an encrypted laptop.
  My spare box is also completely encrypted.
  The spare box is running SSH and such. I usually just scp my data onto the encrypted server then shut the server down. You could use versioning like svn or bzr, but I like it simple.

---

