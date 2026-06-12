---
title: "Adding Files/Folders to a group"
date: 2008-08-29
forum: New to Ubuntu
---

### Post by zero_koop on 2008-08-29
I want to share some files that I have placed in my /home/username/Public folder with other users on the same computer.  I can manually right click on the folders and files and select properties, choose the Permissions tab, and change it to the group I want and that works (other users in that group can now access the file/folder).  But these are my music files and there are thousands of files all in many subfolders.  Clicking on the "Apply Permissions to Enclosed Files" button does not work (does nothing).  How can I change all of the files and subfolders of my Public folder to another Group without doing it manually?  Thanks.

---

### Post by bruce89 on 2008-08-29
```
chgrp -R GROUP FILE
``` is what you want.

---

### Post by zero_koop on 2008-08-29
Thanks, so do I just > cd /home/username first and then use the command > chgrp -R media Public?

---

### Post by zero_koop on 2008-08-30
Ok, I think I've got it figured out.  I did what I said I would do for some reason that worked for my music files, but not my pictures.  My picture files/folders were grouped properly as the command did its job, but access wasn't allowed the files.  This time the "Apply Permissions to Enclosed Files" button worked and successfully changed all the subfolders to a read/write/delete access.

---

