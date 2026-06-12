---
title: "mounting ntfs with RW and accessing a .dd file"
date: 2014-01-09
forum: New to Ubuntu
---

### Post by hookitup on 2014-01-09
Hello all,

I have a slight issue i need some help with.

So i have a drive that has about 500GB of data. It failed on me so i made a DD copy with the program [http://www.datarescue.com/photorescue/v3/drdd.htm](http://www.datarescue.com/photorescue/v3/drdd.htm)
and so i have this file ending in .dd extension, do anybody know how i can mount this or something to view the content in it and extract it ?


Thanks.

---

### Post by Impavidus on 2014-01-09
You won't attract a lot of help when you already mark your thread as solved.

A data recovery tool has to be directed at a device or file, which is more or less the same. Point it at your .dd file. Never tried anything like that myself, so other people will know more.

---

### Post by hookitup on 2014-01-09
shoot idk how it got marked as solved. anybody know how to change that?

---

### Post by sisco311 on 2014-01-09
At the top of the first post click on the **Thread Tools** menu then** Mark this thread as unsolved**.

---

### Post by sisco311 on 2014-01-09
Did you try to mount the file like any other block device?
```
sudo mount path/to/file.dd /mount/point
```
where you have to replace path/to/file.dd with the actual path to the file and /mount/point with an existing mount point like /mnt or any other (empty) directory.

---

### Post by hookitup on 2014-01-10
sisco311 it only says "mark this thread as solved" :( 

and idk if that will work cause basically i have the dd file on a ntfs formatted 1TB drive. does this change anything?

---

### Post by sisco311 on 2014-01-10
The thread has been marked as unsolved.


Did you create the image from the entire disk or just a partition?

Please post the output of: ```
file path/to/file.dd
```
and
```
sudo partx -s -v path/to/file.dd
```

---

