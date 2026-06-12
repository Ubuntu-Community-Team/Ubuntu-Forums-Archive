---
title: "linux unzip command"
date: 2019-07-10
forum: New to Ubuntu
---

### Post by anacondaonline on 2019-07-10
I have a dist.zip
inside this I have:  dist/myapp/filesAndFolders
I want to extract only contents of dist/myapp


In this example I want to get filesAndFolders only.


What flag I should apply in Linux unzip command ?

---

### Post by #&amp;thj^% on 2019-07-10
```
unzip <target-zip-file> '<folder-to-extract/*>' -d <destination-path> 
```
Also see: **man zip**

---

### Post by bunny9000 on 2019-07-11
Or read this:

[https://www.simplehelp.net/2008/12/15/how-to-create-and-extract-zip-tar-targz-and-tarbz2-files-in-linux/](https://www.simplehelp.net/2008/12/15/how-to-create-and-extract-zip-tar-targz-and-tarbz2-files-in-linux/)

Or install 7zip (thinks it's call p7zip in the software center) it's a gui tool.

---

### Post by Dennis N on 2019-07-11
> I have a dist.zip
inside this I have: dist/myapp/filesAndFolders
I want to extract only contents of dist/myapp
...

The archive manager can extract one folder (or one file) from a .zip file. No special utility is needed (unless you really want to use the terminal only). In screenshot, folder2 only is selected for extraction.

---

