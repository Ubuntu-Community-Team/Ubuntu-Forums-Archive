---
title: "Linking Music/Videos to FAT32"
date: 2008-05-16
forum: New to Ubuntu
---

### Post by Verminox on 2008-05-16
I have a dual boot setup and wish to share most files on the intermediate FAT32 partition. 

1. How would I go about creating a link to directories in my FAT32 partition for directories such as /home/verminox/Music, /home/verminox/Videos, etc.

2. Will these links work as if nothing's different in other apps? I mean, for example, if I have a Save/Open dialog, will the shortcuts to these directories work normally?

3. Will I encounter any problems reading/writing from/to the FAT32 partition (because I've read it doesn't handle permissions and stuff)?

4. If I also do the same linking for my Apache htdocs and MySQL data directories to store these files/databases on my FAT partition will that be ok as well?

Thanks :)

---

### Post by .nedberg on 2008-05-16
> **Verminox said:**
> I have a dual boot setup and wish to share most files on the intermediate FAT32 partition. 

1. How would I go about creating a link to directories in my FAT32 partition for directories such as /home/verminox/Music, /home/verminox/Videos, etc.


```
ln -s /media/mountpoint/video /home/verminox/Videos
```
> **Verminox said:**
> 
2. Will these links work as if nothing's different in other apps? I mean, for example, if I have a Save/Open dialog, will the shortcuts to these directories work normally?

3. Will I encounter any problems reading/writing from/to the FAT32 partition (because I've read it doesn't handle permissions and stuff)?

It should work just fine! No problem!

> **Verminox said:**
> 
4. If I also do the same linking for my Apache htdocs and MySQL data directories to store these files/databases on my FAT partition will that be ok as well?

As FAT32 doesn't handle the permissions I would not do this. I am sure you could do it, but my advice is not to.

---

### Post by Verminox on 2008-05-16
Thanks for answers to Q1,2, and 3.

About Q4: You are saying that it's possible, but not recommended for security reasons, right? What are these vulnerabilities? I mean, Apache generally makes sure that only files in the public directory can be executed, right? So what's the problem?

---

### Post by .nedberg on 2008-05-16
I see this as doing a 'chmod -R 777' on the directory holding your webpage. You would be giving everybody write access also. It might not be bad for your system (unless there is a bug in apache), but your webpage might be compromised.

But I am no apache expert. :)

---

