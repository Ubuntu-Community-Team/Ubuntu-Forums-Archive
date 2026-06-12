---
title: "Backing up... error."
date: 2008-05-01
forum: New to Ubuntu
---

### Post by UnWarierMage224 on 2008-05-01
Hi folks, 

I am following the directions here: 
[http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087)

the code I am running: 

```
/media/Recovery/linuxbackup# tar cvpzf backup.tgz --exclude=/proc --exclude=/lost+found --exclude =/backup.tgz --exclude=/mnt --exclude=/sys --exclude=/media
```


I get an error, however when I run the command - 
```
tar: Cowardly refusing to create an empty archive
```

What should I do?

-'Mage

---

### Post by Monicker on 2008-05-01
I see a lot of excludes, but I don't see a specification for what should actually be in the archive.

Try this:

```
/media/Recovery/linuxbackup# tar cvpzf backup.tgz --exclude=/proc --exclude=/lost+found --exclude =/backup.tgz --exclude=/mnt --exclude=/sys --exclude=/media /
```


On the end I just added a specification to start at the root of the filesystem.

---

### Post by UnWarierMage224 on 2008-05-02
Whoops I forgot to include the slash at the end the first time! Included and it worked like a charm! 

Thanks!

-'Mage

---

