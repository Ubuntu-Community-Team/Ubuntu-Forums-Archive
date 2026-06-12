---
title: "Create New Folder and move to trash doesnt work"
date: 2013-07-08
forum: New to Ubuntu
---

### Post by Artpen on 2013-07-08
Hi guys,

I've got two small problems. I have two 1Tb HDD in Raid 1. I have /data partition on it, BUT:

- I can't move files to trash from this partition, only permanently
- I can create folders and files at this partition , but Create New Folder in the menu is still greyed out

If you need more specific information to help me, I can provide it.

Thanks

---

### Post by Artpen on 2013-07-09
Well the problem 2 was solved by itself after Ubuntu update.
Problem 1 still dont know what can I do about it.

---

### Post by dannyboy79 on 2013-07-09
where are you mounting the raid array, which folder? what are the permissions, owner, and group of that folder? what is the exact error you get when trying to move stuff to your recycle bin?

---

### Post by Artpen on 2013-07-09
Raid Array mounted at /data
drwxr-xr-x   4 root root  4096 Jul  7 15:35 data

But inside /data I have /data/main  folder where all my files
drwxr-xr-x 7 rgorshkov rgorshkov  4096 Jul  9 11:53 main

When I am trying to delete files from this folder I get :
**Cannot move file to trash, do you want to delete immediately?**

---

### Post by dannyboy79 on 2013-07-09
hmmm, i wonder if it's because the parent folder is owned by root OR the file you are trying to delete is to large to fit in the recycle bin so it's only choice is to delete immiately.

---

### Post by Artpen on 2013-07-09
Well I tried to change /data ownership and I still cant delete files to bin.
I heard that you should create .trash folder in order to be able move files to bin?

---

### Post by dannyboy79 on 2013-07-09
do you have a folder located within your home directory called .local? it'll be hidden, so in nautilus you'll have to show hidden files/folders. then it's share, then Trash, then files. what are the permissions of each of those folders?

---

### Post by Artpen on 2013-07-10
drwxr-xr-x  3 rgorshkov rgorshkov 4096 Jul  6 21:43 .local
drwx------ 5 rgorshkov rgorshkov   4096 Jul  7 17:22 Trash

---

### Post by Artpen on 2013-07-10
My /home drive and /data drive atr to defferent hdd

---

