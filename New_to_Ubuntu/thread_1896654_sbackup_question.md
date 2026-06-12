---
title: "sbackup question"
date: 2011-12-17
forum: New to Ubuntu
---

### Post by Old Jimma on 2011-12-17
Hi Ubuntu Community:

I've configured my system so that the operating system is on an SSD drive and my /home folder is on a HD drive.

I want to use sbackup, and it gives alot of nice options for backing up files.

My question is: if you want to restore stuff, how will sbackup know what portions that were backed up go to your SSD and which portions to to your HD when you've got a system configured like mine?

ALso, if I only backup my /home directory, if I do a restore, how will sbackup know to write those files to my HD an not on my SSD?

Thanks!
Phil de Duluthistan

---

### Post by searchfgold6789 on 2011-12-17
Any backup program should restore the files to the original directory they were in unless you tell it to do otherwise. SBackup gives you the option to include the original path name on the backed up files. As long as you still have your partitions mounted where they should be, these paths will be backed up to the proper hardware.

---

### Post by Zill on 2011-12-17
Phil Smith:  You should also be aware that the default path for the SBackup archive is /var/backup/.  If you do not change this then presumably this directory will be on your SSD drive.  So, your backed-up (compressed) data from your /home directory will saved on your SSD drive - just make sure you have enough space for this.

Of course, you can configure SBackup to save the archive anywhere you like.  eg. another internal or external hard-drive or another networked PC etc.

---

### Post by Old Jimma on 2011-12-30
Thanks, Zill!

---

