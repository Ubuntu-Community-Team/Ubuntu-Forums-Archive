---
title: "PHP: Determine if directory contents changed"
date: 2008-01-10
forum: Programming Talk
---

### Post by x1a4 on 2008-01-10
Hi,

Using PHP4.4.6, Is it possible, and if so how, to determine if the contents of a directory have changed?  

Thank you.

---

### Post by LaRoza on 2008-01-10
You could use [http://www.php.net/manual/en/function.scandir.php](http://www.php.net/manual/en/function.scandir.php) or other such functions and put the contents in a file, then write a function to test the contents against that file.

---

### Post by popch on 2008-01-10
The file system usually keeps a time stamp for each directory entry which registers the date and time the object was last changed. This applies both to files and directories. In some circumstances just checking the time stamp of the directory might suffice. Can you read the date and time the entry was last changed in PHP?

---

