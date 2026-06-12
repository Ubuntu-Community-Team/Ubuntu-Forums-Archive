---
title: "bleachbit crash on freespace wipe recovery"
date: 2014-07-04
forum: New to Ubuntu
---

### Post by JamButty on 2014-07-04
Running Bleachbit 1.2 on Ubuntu 14.04
While doing a wipe freespace operation, system crashed due to overheating. Now I have a 35 GB file at home level that can only be from that. System appears to be functioning normally, but I am leery of restarting Bleachbit and/or trying to delete that huge file.
Is there any recovery procedure needed?
Have dug around here and in other forums and found no answer.

thanks

---

### Post by Impavidus on 2014-07-05
I saw other people reporting that the wipe freespace operation doesn't work very well and gives some huge files. It is labeled as experimental, right? You could try renaming that huge file or move it somewhere else. If everything still works, it's safe to delete it.

---

### Post by Ashwij on 2014-07-07
It is an experimental feature and does crash so avoid it. The huge file may be because some wiping portion got renamed by Ubuntu due to the crash. Check if all ur home files are present and then delete the file, its ok. But delete it using gksudo nautilus and then delete, its safe. No system file can be that large

---

