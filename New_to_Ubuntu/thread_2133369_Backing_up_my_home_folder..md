---
title: "Backing up my home folder."
date: 2013-04-08
forum: New to Ubuntu
---

### Post by Absolute Terror on 2013-04-08
Whenever I try to sudo / kdesudo with Dolphin it gives me errors for output and changes all of the permissions in my home folder to root. I did not have this problem in normal Ubuntu.

What would be the best way to back up all folders in /home/username? I just want the contents of the folder, not the "username" folder itself. I also don't want to copy any hidden files or folders.

---

### Post by carl4926 on 2013-04-08
Why su?
Woking in /home/username*/
does not require su, just copy and paste them where you want them

---

### Post by Absolute Terror on 2013-04-08
It does require permissions to write to the external drive if I am using ext4.

---

### Post by carl4926 on 2013-04-08
It shouldn't if you have ownership of the partition you are copying to
I have no trouble copying from my home to an external ext4 for backup
You probably need to chown it
I have my external with a Volume Label, so it always mounts as /STORE
I used chown -R myself to that

---

### Post by Absolute Terror on 2013-04-08
```
chown -R mynamehere /media/VolumeName
```

Like this?

---

### Post by carl4926 on 2013-04-08
Yes
sudo though

---

### Post by carl4926 on 2013-04-08
Personally I would cd to /media so that your chown on just /volume

Then it's

sudo chown -R myname STORE

---

