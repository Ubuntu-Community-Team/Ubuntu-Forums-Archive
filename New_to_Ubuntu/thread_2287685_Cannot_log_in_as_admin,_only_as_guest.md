---
title: "Cannot log in as admin, only as guest"
date: 2015-07-21
forum: New to Ubuntu
---

### Post by Patrick_S_L_Ghose on 2015-07-21
I'm using Ubuntu 14.04 LTS. I cannot log in as administrator but only as guest. It was working fine two days ago. No one else uses my computer. And sorry, but am a newbie so would appreciate help and advise that would make sense to me.

---

### Post by TheFu on 2015-07-21
Not sure how to help based on the words above. Sorry.
[http://www.dedoimedo.com/computers/ultimate-linux-guide-for-windows-users.html](http://www.dedoimedo.com/computers/ultimate-linux-guide-for-windows-users.html) - might help?

---

### Post by ajgreeny on 2015-07-21
I have moved your thread from "Security" to "New to Ubuntu", as it is not a security query, and you are new to this OS.

It is not possible to diagnose your problem, however, with the lack of information you have given us.
Please tell us much more.

What OS is this with which desktop environment?
Have you kept it updated with the update-manager (or other system tool)?
Have you ever used **sudo** to open an graphical program of some sort and if so what was it?
Please boot to recovery mode from the grub menu and choose the command line interface; then from that run command ```
ls -al /home/*user*
``` where *user* is your usual username that is failing at the moment.  That will show us if there is a problem of folder and file ownership in your home.

---

