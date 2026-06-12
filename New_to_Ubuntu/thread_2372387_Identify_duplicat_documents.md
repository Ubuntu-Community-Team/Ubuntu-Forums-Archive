---
title: "Identify duplicat documents"
date: 2017-09-24
forum: New to Ubuntu
---

### Post by sed_faster on 2017-09-24
Hello folks,

I need identify duplicate files on my system. For example, I have file "document_all_pages.pdf" and I need know if this document exist on my disks, even with a different name. For this task I am thinking use the sha256sum or md5sum. Maybe I create a script where I step as variable the name the document "document_all_pages.pdf" and this script calculate the string number, through md5sum or sha256sum, and find this number inside the file .txt. On this file, to save time, I have a list with all my content and respective string numbers referring to each file on my disk.

This is a good way? What do you think about this method?

Thanks

---

### Post by kevdog on 2017-09-24
Within your target directories -- or paths, you are going to have to calculate the hash of every known file and then write the result to a file.  I'd then sort the file by hash type since this will give you the duplicates. You can then delete or move the duplicates or perform whatever you want with them if you wish.

---

### Post by ajgreeny on 2017-09-24
A much simpler way to do this is to install **fdupes** and use that to quickly find duplicates in specific directories. It is pretty fast; I have just used it to find dupes recursively in my Pictures folder (17000 photos) in about 60 seconds or less.

Once you have installed it run **man fdupes** to see all the options, etc etc.

---

### Post by sed_faster on 2017-12-26
Exist any alternative to the fdupes? Because fdupes use md5sum, this is really reliable? it would not be better sha5sum? thanks

---

### Post by Holger_Gehrke on 2017-12-27
fdupes does a file size comparison then a check of the md5 sums and finally a full comparison of the files with matching size and md5sum. The first two stages of this process are meant to reduce the number of full comparisons necessary to find duplicates. So yes, this is as reliable as it gets.

Holger

---

