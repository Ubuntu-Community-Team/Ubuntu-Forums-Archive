---
title: "Multiple file zips"
date: 2008-08-05
forum: New to Ubuntu
---

### Post by Vendeta on 2008-08-05
Hey guys, I have a folder on desktop with a bunch of files that are as follows

File.z01
file.z02
file.z03
........
file.z35

Clearly its a zip in multiple files. How can i unzip it and get its contents?
Tottal noob question lol...
thanks for any and all help.
Oh im on ubuntu 7.10 if that matters.

---

### Post by st33med on 2008-08-05
You can just go to it via Nautilus (your file manager) and double click it to launch the archive manager. Hit the Extract button at the top and specify where you want to place the folder (usually in your home folder)

or (I think this works):
```
tar -xvf <.zip file>
```

---

### Post by Vendeta on 2008-08-05
I tryed to double click and it says it can not be open. Please help

---

### Post by kostkon on 2008-08-05
Are you sure that it's a zip file? When I need to extract a multiple zip file I just extract the first file and then archive manager automatically extracts and combines all the rest of the files.

---

### Post by st33med on 2008-08-05
Why does it say it can't be opened? Does it say 'Permission Denied'?

Try my terminal option:
```
cd <directory_of_zip>
unzip <zip_archive> -d ~
```
For example, I have a file.zip archive in my /tmp folder:
```
cd /tmp
unzip file.zip -d ~
```

---

### Post by Vendeta on 2008-08-05
End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
 

Grr i know the files are proper... what am i to do?

---

### Post by oldos2er on 2008-08-05
As the error message says, try opening the last file in the series instead of the first.

---

