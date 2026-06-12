---
title: "tortoise"
date: 2008-07-22
forum: Programming Talk
---

### Post by ben22 on 2008-07-22
Hi,

I am looking for a command line possibility not to have to manually perform all changes to folder structure files of the working copy, so that changes are automatically present in the repo after committing.

In other words:
- I have a workingcopy folder "ben".
- I delete the subfolder "deletefolder" from "ben"
- With tortoise I can simply mark the working copy folder, then click add, and Tortoise automatically adds / removes the respective changes to the folders and files.

What if there is  no tortoise on Ubuntu?

SOLUTION FOR ADDING: For adding I found out how to do that: "svn add *", it then adds the new folder and prompts for existing folders and files that they already exist.

NO SOLUTION FOR REMOVING: Is there a possibility to delete a folder from the working copy folder, then not having to remove the deleted folder with "svn remove deletefolder" and then to commit so that the folder will also be deleted from the repo.

If any out there know how to handle the problem, let me know. If there is a good GUI for svn administration like tortoise I would also be happy. (rapidsvn, kdesvn, svnworkbench did not support what I described above).

Best,
Ben

---

### Post by pmasiar on 2008-07-22
pysvn workbench is multi-platform client to Subversion (and you should read "how to ask questions" to learn at least better titles to your posts).

---

### Post by The Cog on 2008-07-22
I use **rapidsvn**, which seems quite a reasonable GUI. I also use **meld** as my file comparator rather then the default rapidsvn one. I think they're both at least worth a try.

---

### Post by mssever on 2008-07-22
I use ```
svn rm whatever
``` which works for me. Your question is unclear, so I don't know if this answers your question. I tried RapidSVN once and decided that it didn't offer anything I couldn't do easier from the command line. I haven't seen any point in trying other GUI svn clients when the svn command works so well.

---

