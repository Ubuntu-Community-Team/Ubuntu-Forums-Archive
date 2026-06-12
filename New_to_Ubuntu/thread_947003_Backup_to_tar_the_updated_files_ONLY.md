---
title: "Backup to tar the updated files ONLY"
date: 2008-10-13
forum: New to Ubuntu
---

### Post by malleeblue on 2008-10-13
In [this post]("http://ubuntuforums.org/showpost.php?p=3812934&postcount=19") mdpalow wrote that it's possible to "copy updated files to another drive using tar".

I use tar to take daily backups of some of my files but when I run the below command it's still copying all the files to the tar again.

```
sudo tar uvpf /media/BACKUP-1/backupFLASHDRIVE.tar /media/FLASHDRIVE
```

Could you please tell me what I'm doing wrong and explain how, when my backup runs, I can get it to only copy the updated files?

---

### Post by unutbu on 2008-10-13
The tar command "tar uvpf" uses the update flag. According to
[http://www.gnu.org/software/tar/manual/html_section/Advanced-tar.html#SEC57](http://www.gnu.org/software/tar/manual/html_section/Advanced-tar.html#SEC57)
> 
&#8216;--update&#8217; (&#8216;-u&#8217;) is not suitable for performing backups for two reasons: it does not change directory content entries, and it lengthens the archive every time it is used.

To do incremental backups with tar, see
[http://www.gnu.org/software/tar/manual/html_section/Backups.html#SEC87](http://www.gnu.org/software/tar/manual/html_section/Backups.html#SEC87)
(in particular, section 5.2)

However, I wonder if a different tool such as rsync might be easier to use.
For example,
```

rsync -a /media/FLASHDRIVE/ /media/BACKUP-1

```
would copy all files from /media/FLASHDRIVE/ to /media/BACKUP-1.
One subsequent runs only files that have changed will get transferred.

---

