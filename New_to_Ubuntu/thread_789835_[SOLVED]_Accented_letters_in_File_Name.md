---
title: "[SOLVED] Accented letters in File Name"
date: 2008-05-10
forum: New to Ubuntu
---

### Post by fballem on 2008-05-10
Are accented characters allowed in file names?

The reason that I'm asking is that some of the files that I'm bringing over from Windows are identified as having invalid coding.

Thanks,

---

### Post by sdennie on 2008-05-10
They are allowed but, I don't recommend them.  Some file systems will use UTF8 while others will use ISO8859-1 which means that the characters will look strange depending on whether or not the two file systems are using the same character encoding.

---

### Post by fballem on 2008-05-10
Looks like I have to go through my files and media to remove the accented names.

Thanks

---

### Post by daengbo on 2008-05-11
You might not have to do that. You may just need to mount the Windows partition with the right encoding.

In /etc/fstab, my cdrom looks like 
> /dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0


I would change "utf8" (at the end of the line) to ISO8859-1

---

### Post by fballem on 2008-05-11
> **daengbo said:**
> You might not have to do that. You may just need to mount the Windows partition with the right encoding.

In /etc/fstab, my cdrom looks like 


I would change "utf8" (at the end of the line) to ISO8859-1

Thanks for this. In solving some other problems that I was having, I ran across some other information that was most helpful. I have put it in the following post: [http://ubuntuforums.org/showthread.php?p=4932265#post4932265](http://ubuntuforums.org/showthread.php?p=4932265#post4932265)

---

