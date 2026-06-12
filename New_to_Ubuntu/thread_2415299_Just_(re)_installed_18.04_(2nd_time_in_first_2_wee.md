---
title: "Just (re) installed 18.04 (2nd time in first 2 weeks). Can't access data on externals"
date: 2019-03-23
forum: New to Ubuntu
---

### Post by dylan2k on 2019-03-23
i know (thanks the gods) that the data is still there because I have another (Wxxxxxxs) computer to check on, but I, admittedly, mounted them incorrectly using instructions from another forum and now they are read-only, despite saying otherwise.  Is there a way to undo the mounting process that I did and start from scratch?  I have backed up all the data if I have to format them, but I'd obviously rather not have to do that. They are at /dev/sdb1 and /dev/sdd1 respectively.  They are both NTFS, according to sudo blkid.

---

### Post by Impavidus on 2019-03-24
If I understand you correctly, you have some external drives, formatted NTFS, that you can only mount read-only in Ubuntu, whilst in Windows they work correctly. NTFS is a Windows filesystem, so you'll have to use Windows to fix them. Plug them into a Windows computer, you may have to run a filesystem check, then properly remove them by clicking eject or savely remove or something like that and unplug them only after you get the message that they can be savely removed.

---

### Post by yancek on 2019-03-24
Another possibility is that you were using a windows system that hibernates and the filesystems were left mounted by windows.  This is common, default behavior on windows 10 so if the windows computer you used was 10 (which you don't indicate?), that's another possibility.  More likely to resolve the problem with the suggestion above.

---

