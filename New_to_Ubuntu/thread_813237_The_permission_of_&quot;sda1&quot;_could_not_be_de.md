---
title: "The permission of &quot;sda1&quot; could not be determine"
date: 2008-05-30
forum: New to Ubuntu
---

### Post by wariskampar on 2008-05-30
i would like to set permission for my WinXP partition. but i just see the above message in Permission Tab. When i check, all my other partition have the same character. it seem like i can only set permission for folder. what should i do to enable this feature

---

### Post by bjm1904 on 2008-05-30
Do your have the relevant permissions? If not, then you can head to the terminal:

sudo su

then use chmod to alter the permissions. Check the man page or try chmod -help to get all the relevant parameters you need.

---

### Post by NormR2 on 2008-05-30
Look at previous posts on /etc/fstab file and the mount command.
They should help you solve your problem.

---

