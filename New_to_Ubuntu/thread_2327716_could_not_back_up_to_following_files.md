---
title: "could not back up to following files?"
date: 2016-06-13
forum: New to Ubuntu
---

### Post by devrekli on 2016-06-13
Hello. I can not get a full backup. It does not backup many files. How can I solve this problem? thanks.

Screenshot: [http://i.imgur.com/mH1Srmv.jpg](http://i.imgur.com/mH1Srmv.jpg)

---

### Post by Habitual on 2016-06-13
The "errors" indicate you attempted backup of system files, to which you don't have access to.
You ran the backup tool as user or root (or did it prompt for privilege escalation)?
Have a look at some excellent options at [http://askubuntu.com/questions/2596/comparison-of-backup-tools](http://askubuntu.com/questions/2596/comparison-of-backup-tools)

---

### Post by oldrocker99 on 2016-06-13
If you're trying a complete backup of the whole disk, you **must** have superuser access (with sudo). The most important thing to back up is your /home/username folder. which you don't need special permissions to do. You can always reinstall and restore /home, if need be. I use grsync for my backups and it works very well.

---

### Post by devrekli on 2016-06-14
> **Habitual said:**
> The "errors" indicate you attempted backup of system files, to which you don't have access to.
You ran the backup tool as user or root (or did it prompt for privilege escalation)?
Have a look at some excellent options at [http://askubuntu.com/questions/2596/comparison-of-backup-tools](http://askubuntu.com/questions/2596/comparison-of-backup-tools)

> **oldrocker99 said:**
> If you're trying a complete backup of the whole disk, you **must** have superuser access (with sudo). The most important thing to back up is your /home/username folder. which you don't need special permissions to do. You can always reinstall and restore /home, if need be. I use grsync for my backups and it works very well.

How do I run as root? I tried **nautilus** and **sudo su** in terminal :( thanks

---

### Post by Habitual on 2016-06-14
gksudo <backup_program>

---

### Post by SeijiSensei on 2016-06-14
"sudo rsync -av source target" works for me.

---

### Post by Habitual on 2016-06-14
grysnc has a "Run as Super User" option.

```
sudo apt-get install grsync
``` that I presume to mean I would not use
gksudo <backup_program> on.

but if you don't understand rsync and its numerous complexities, then grsync may not work for you,
unless you learn some c-line rsync to "compliment" the use of grsync.

[Simple UNIX/Linux Backup with rsync]("http://rsync.net/resources/howto/rsync.html")

Hope that helps.

---

### Post by devrekli on 2016-06-14
> **Habitual said:**
> gksudo <backup_program>

thanks for help.

Can you help me with this? [http://ubuntuforums.org/showthread.php?t=2325339](http://ubuntuforums.org/showthread.php?t=2325339)   I think that the authority problem.

---

### Post by Habitual on 2016-06-15
Looks fixed from here. I didn't study the post.

See also [https://help.ubuntu.com/community/MysqlPasswordReset](https://help.ubuntu.com/community/MysqlPasswordReset)

Being new to Ubuntu Linux, you really should bookmark [https://help.ubuntu.com](https://help.ubuntu.com)
I'm not being a "meany", it really all starts there. ;)

---

