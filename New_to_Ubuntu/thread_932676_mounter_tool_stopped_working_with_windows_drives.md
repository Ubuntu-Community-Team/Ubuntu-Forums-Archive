---
title: "mounter tool stopped working with windows drives"
date: 2008-09-28
forum: New to Ubuntu
---

### Post by fatagnus on 2008-09-28
I have Ubuntu Hardy, and updated recently, then suddenly I can't mount Windows drives with the disk mounter tool, but I could before. A blank alert window appears,and half a second after, a new, different alert window appears with a 'details' view with the message 'only the root user can mount /dev/sda1 in /media/sdb1'.

Do I have to forget about using the gui for mounting those drives, or is there something I can do to restore its functionality (mount+unmount)?

[edit: seems like windows didn't shutdown correctly, or at least it didn't let the drives free.

I installed ntfsprogs, then i ran 'sudo ntfsfix /dev/sda1' (the same on each ntfs drive) then 'mount -t ntfs-3g /dev/sda1 /media/sda1' and I was able to read/write to the drives again, but without the GUI. For using the GUI, I just had to reboot on windows, shutdown it 'cleanly' then boot on Ubuntu again.]

---

### Post by Pro-reason on 2008-09-28
Please use the thread menu to mark this as Solved.

---

