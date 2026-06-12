---
title: "Changing my Hostname (computer name)"
date: 2011-09-11
forum: New to Ubuntu
---

### Post by foreman25 on 2011-09-11
Trying to change my host name. Followed the tutorial from Google, but it doesn't want to work. I went to the Terminal and typed : gksu gedit /etc/hostname which led me to a window to change the name. I did, then saved the file. Then typed in the terminal : gksu gedit /etc/hosts and it brought me to the final window. I changed the name, saved the file and exited the window. Yet the terminal continues to recognize me as my original hostname. I might just need sleep. But if anyone has any tips they would be greatly appreciated.

---

### Post by papibe on 2011-09-11
My guess is you need to reboot in order for the system to get its new name.

Regards.

---

### Post by hakermania on 2011-09-11
If you open a new terminal window (or I think 'source ~/.bashrc') you'll see your new hostname

---

