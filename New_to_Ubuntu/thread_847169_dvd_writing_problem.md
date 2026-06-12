---
title: "dvd writing problem"
date: 2008-07-02
forum: New to Ubuntu
---

### Post by Falc7 on 2008-07-02
I am trying to make a DVD that will play in a DVD player using K3B.
I opened K3B up, clicked 'new dvd video' project, put the files in (which are avi), and clicked burn. I get this error message:

The project does not contain all the necessary DVD video files
The resulting dvd will most likely not be playable on a hifi dvd player
Could not determine the size of the resulting dvd image.

And the DVD dosen't burn.
What am i doing wrong?

---

### Post by damis648 on 2008-07-02
The videos have to be correctly encoded to make a playable DVD. To make a playable DVD, install DeVeDe.

---

### Post by Falc7 on 2008-07-03
I have just burned it with devede, but when i put it in the DVD player, it says 'wrong disk', what could be causing this?

edit: i just found out if failed to burn, hang on a sec

edit2: When making a disk it asks for a place devede can make an image, but it says don't use a FAT32 system, doesen't the whole of ubuntu use FAT32 file system?

---

### Post by damis648 on 2008-07-03
No, Ubuntu uses the Ext3 or Ext2 filesystem. Just put it in your home directory.

---

### Post by Falc7 on 2008-07-05
ok, done that, it made an iso, so i should just write this iso file to the dvd using brasero or k3b right?

Also, i have another small question, i have a file in the wastebasket that i can't delete, it tells me i don't have permission, how can i delete it?

---

### Post by MepisReign on 2008-07-05
To get ownership of the files contained on the Trash can and therefore be able to delete them

[http://ubuntuforums.org/showthread.php?t=817075](http://ubuntuforums.org/showthread.php?t=817075)

Best Regards,

MepisReign

---

