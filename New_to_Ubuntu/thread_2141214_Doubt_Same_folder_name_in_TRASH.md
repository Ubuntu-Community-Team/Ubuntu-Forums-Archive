---
title: "Doubt: Same folder name in TRASH"
date: 2013-05-02
forum: New to Ubuntu
---

### Post by pmohankumar on 2013-05-02
Hi friends,
 I am having a doubt. 
Inside filesystem, we cannot save two folder's with same name. for example, inside home folder we cannot save two folder's with same name mohan, but i found many folder's with same name inside the trash.
Pls explain the concept of TRASH.

Also pls mention the location of trash.

---

### Post by JOHNNYG713 on 2013-05-02
say you have made 3 "untitled" folders in the past, and throw them in the the trash, yes you can have all 3 same name in the trash, Trash is not an active system folder ! it is static, I believe trash is in home/.local, I use the delete option most of the time, trash, is in case you want to retrieve something you might not really want to throw away ! delete option is irretrievable !

---

### Post by pmohankumar on 2013-05-02
Hi friends,

Kindly provide a script to delete files in trash, which could run in cronjob.

---

### Post by grahammechanical on 2013-05-02
The files are not moved at all. They are still at their location on the hard disk. The reference to that location is removed and stored at a location called Rubbish Bin. Future write operations to the hard disk are not allowed to overwrite those locations. This is how it is possible to restore files moved to the rubbish bin. It also explains why moving files to the rubbish bin does not free up space on the hard disk. We need to empty the rubbish to free up that space.

When we empty the rubbish bin the references to the locations are wiped away. This allows future write operations to the hard disk to overwrite the locations and so destroy the data at the locations.

Something different happens when we move a file on another partition to the rubbish bin. We get a warning that the file is going to be deleted. The location of the data is not going to be moved into the rubbish bin of the file system that we are using. Future write operations to that partition will be allowed to overwrite the space occupied by that data.

Regards.

---

