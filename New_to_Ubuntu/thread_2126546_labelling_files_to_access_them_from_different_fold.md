---
title: "labelling files to access them from different folders."
date: 2013-03-17
forum: New to Ubuntu
---

### Post by s1wood on 2013-03-17
I have a lot of large pdf files for historical research and I sort them into folders either according to the type of material (history, biography) or the year or section the material relates to. Some files relate to more than one year, is it possible to label them in some way so I can access them from more than one folder without having multiple copies? 



Susan

---

### Post by black veils on 2013-03-17
[this]("http://askubuntu.com/questions/191621/managing-a-large-collection-of-pdf-files") thread resulted in the choice of:

[zotero]("http://www.zotero.org/") but i dont really understand how it is installed. there is various information around, depends on what you want.

---

### Post by Merrattic on 2013-03-17
Google Drive ? Allow you to use labels as in gmail.

Whhile we wait for Google to provide a linux client, it is possible to sync with hard drive on Linux:

[http://www.howtogeek.com/130380/how-to-use-google-drive-on-linux-2-unofficial-solutions/](http://www.howtogeek.com/130380/how-to-use-google-drive-on-linux-2-unofficial-solutions/)

---

### Post by s1wood on 2013-03-17
I've tried Zotero before and couldn't get the hang of it. I've looked at it again but it seems to be just web-based and all my stuff is on the HDD. Ditto Google drive.
I've just had a look in the software centre - anyone know anything about Gcstar collection manager? 

Susan

---

### Post by SeijiSensei on 2013-03-17
If you're asking simply about how to handle this in the file system, use symbolic links.

Suppose you have two folders, 19th_century_us and 19th_century_europe, both at the same "level" in the directory tree.  If you have a file about the Louisiana Purchase, you could put it in the first one, then create a "symlink" to it like this:

```

cd /path/to/19th_century_europe
ln -s ../19th_century_us/louisiana.pdf

```

Now the file will appear to reside in both locations.  This method creates a "soft" link.  There are also "hard" links, but I never use those.

If you're looking for a database-driven solution or something equally complex, I'm afraid I cannot help with that.

---

### Post by Impavidus on 2013-03-17
+1 to SeijiSensei

Make one directory tree with the material sorted according to type an a second tree with symlinks to every file, the symlinks sorted according to year/section (or vice versa).

Instead of symlinks you can use hardlinks. The advantage of hardlinks is that when you move a file to a different location in one of the trees it will remain correct in the other. If you use symlinks moving the link will work, but moving the real file will make the link in the other tree invalid. So if you use symlinks, make sure you put the links in the directory tree you are most likely to change.

---

### Post by s1wood on 2013-03-17
I thought there must be something like that. I shall have to go away and play with this, I am not sure my understanding of the terminal is up to it.Can you explain hardlinks please?

Susan

---

### Post by Impavidus on 2013-03-18
Every file on a linux system has an associated inode. This contains the permissions, a reference to the physical location of the file on the disk (if located on the disk) and some other information, but not the file name. A directory contains file names with associated inode numbers. If multiple file names (possibly in multiple directories, but on the same partition) refer to the same inode, you have multiple hard links to the same file. A file is deleted when all hard links are removed (and no process has the file opened). In symbolic (or soft) links a file is not referenced by it's inode number multiple times, but once by it's inode number (the only hard link, in other words, the real location of the file) and one or more times by it's path (the symbolic links).

If for example you have file name A and file name B, both refering via hard links to the file with contents "foo", and you rename file A to A.old and create a new file A with contents "bar", them file names A.old and B will both refer to the same file with contents "foo" and file name A will refer to the file with contents "bar". If you then delete A.old the file will continue to exist, but only under the name B.
If you have a file named A with contents "foo" and a symlink B refering to A, both will contain "foo". After renaming A to A.old symlink B will become invalid and after creating a new file A with contents "bar" A.old will contain "foo" and A and B will both contain "bar". If you then delete A its contents will be lost, despite B still existing, and B will become an invalid link again.

You can read [http://en.wikipedia.org/wiki/Inode](http://en.wikipedia.org/wiki/Inode) and the references therein.

Most people (like me) almost never use hard links, but in your case they may be the best solution. However, it [seems]("http://ubuntuforums.org/showthread.php?t=2018250") that creating hard links from the GUI isn't well supported (it can be considered a pretty advanced feature), so if you're unfamiliar with the command line it may be easier to use symbolic links after all.

---

### Post by vanadium on 2013-03-18
Zotero is specifically designed for what you want to do - maintain and organize references. You will have the additional benefit that you easily can reference the various items when you write a research report. It does work with local collections, stored on your hard disk.

Maintaining this directly through file system links will be tedious and limit your flexibility in organizing and searching compared to a system such as zotero.

---

### Post by s1wood on 2013-03-18
Thanks everyone. I've come to the conclusion that the file link system, though so beautifully explained, is probably beyond me.
I'm trying out  Gcstar collection manager which catalogues the stuff and allows me to search by tag.

Thanks again,

Susan

---

