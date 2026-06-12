---
title: "need help making a list of folders, sub folders and files using ls and/or cat"
date: 2012-11-25
forum: Programming Talk
---

### Post by s1baker on 2012-11-25
hi

How can I make a text list of all the directories and sub-directories with the files included?


Example:
```

Main folder/
 file_in_main_folder-1
 file_in_main_folder-2
 file_inmain_foldrer-3
 sub_folder1/
   file_in_sub_folder1-1
   file_in_sub_folder1-2
   file_in_sub_folder1-3
 sub_folder2/
   file_in_sub_folder2-1
   file_in_sub_folder2-2
   file_in_sub_folder2-3

etc...etc...

```

Otherwords, I want a text file of a listing of all the files under their approproate folders so that I
can do a text search on this list file and find a file and know what subfolder it exists in.
I don't need the chmod or anything other than the folder/file names ( although it really doesn't matter ) 

Thanks

---

### Post by Vaphell on 2012-11-25
*tree* command

```
tree *dir(s)* > file
```
to dump the output to file.

---

### Post by s1baker on 2012-11-25
thanks Vaphell.
just what I need.

---

