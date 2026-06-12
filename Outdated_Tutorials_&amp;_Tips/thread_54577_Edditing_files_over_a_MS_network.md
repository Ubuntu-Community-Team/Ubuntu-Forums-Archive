---
title: "Edditing files over a MS network"
date: 2005-08-05
forum: Outdated Tutorials &amp; Tips
---

### Post by TreeFrog on 2005-08-05
Hi,
I'm new to all this so please dierct me to a place if the answer is already there.

Ubuntu is installed on me desktop. It is the quiet time of year so I thought why not try something new.

I want to access and modify the files on a server. (Excel and Word only)
I can see the files. 
I can copy the files to a local drive.
However I cant open and edit the files directly on the win2000 server.

Thanks to anyone who can point me in the right direction.

Treefrog.

---

### Post by Lord Illidan on 2005-08-05
I'm not sure, but if it is Windows 2000, then it uses NTFS, which probably means that write support is disabled, as writing to NTFS under Linux is still experimental.

---

### Post by TreeFrog on 2005-08-05
That sounds like it alright.
Is there really nothing that will bridge the gap??
If it was FAT32 would it be more likly to work??

---

### Post by Sam on 2005-08-05
If it's over a network, this is Samba which handles the files for writing, no matter the drive is NTFS or not.

Can you copy the file locally, modify it, then copy it back to the server ? If not, you need to set on your server a read-write access on the share, otherwise it's your application which doesn't handle the smb protocol (used by Samba).

---

