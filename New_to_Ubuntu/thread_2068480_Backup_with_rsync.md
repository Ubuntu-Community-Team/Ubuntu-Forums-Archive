---
title: "Backup with rsync"
date: 2012-10-09
forum: New to Ubuntu
---

### Post by nhpropwn on 2012-10-09
Hi guys,
I want to make backup of files/directories and then restore it removing all present changes and new files and directories. 

example: make /home backup and after time restore how it was before

How can I do it with command line: rsync, cp or with stomething else

Sorry for my english :(

---

### Post by NikTh on 2012-10-09
Hi ,

with rsync 

```
rsync -aS <target directory> <destination directory>
```Parameters -a -S 
from man rsync
```
 -a = archive mode ; equals to -r # means recursively
-S = handle sparse files efficiently
```above command will effectively copy ALL your files from "target directory" (including hidden files-configuration files) to the "destination directory" .
Command is reversible for restore , although some users including other parameters for restore such ```
--ignore-existing = skip updating files that exist on receiver
```Take a look in manual page ```
man rsync
``` and make some tests (in a testing folder) . 

Thanks

---

### Post by Lars Noodén on 2012-10-09
There are some examples here:

[https://help.ubuntu.com/community/rsync](https://help.ubuntu.com/community/rsync)

---

### Post by centaurusa on 2012-10-09
> **nhpropwn said:**
> 
I want to make backup of files/directories and then restore it removing all present changes and new files and directories. 

How can I do it with command line: rsync, cp or with something else


Take a look at Back In Time which is a graphical front end for rsync and works extremely well.  See, for example:

[http://linuxnorth.wordpress.com/2012/03/12/back-to-the-future/](http://linuxnorth.wordpress.com/2012/03/12/back-to-the-future/)

---

