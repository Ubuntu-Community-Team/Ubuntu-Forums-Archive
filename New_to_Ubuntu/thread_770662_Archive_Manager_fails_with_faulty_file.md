---
title: "Archive Manager fails with faulty file"
date: 2008-04-27
forum: New to Ubuntu
---

### Post by freesitebuilder on 2008-04-27
I'm trying to backup before upgrading - Simple Backup (which I used last time) doesn't like my USB external hard drive, not does HUBackup. So I've reclaimed some space from my XP internal drive, and partitioned it as ext3.

Still can't get Simple or HUB to work, so I thought I'd simply archive manually - but the archive manager (file roller) gives this part way through:

An error occurred while adding files to the archive.
(list of files with "permission denied" in my childrens home folder)
tar: Error exit delayed from previous errors
mv: cannot stat `.gz': No such file or directory

TIA - I hate backups!

---

### Post by lamalex on 2008-04-27
Try running the archive manager as super user. Open a terminal and run sudo file-roller

---

### Post by freesitebuilder on 2008-04-27
I get the same results with that - it starts OK, but once the progrss bar gets about three-quarters of the way across, it switches to a back and forwards bar, although it still says "adding files". Then eventually it gives the file error message.

---

