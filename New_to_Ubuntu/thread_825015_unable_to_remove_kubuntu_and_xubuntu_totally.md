---
title: "unable to remove kubuntu and xubuntu totally"
date: 2008-06-10
forum: New to Ubuntu
---

### Post by hazman on 2008-06-10
i been trying all flavours of the buntu's and gone back to ubuntu.but now am stuck with all kde and kcfe stuff and cannot remove.can not even use gdm as apparently its not running. tried "sudo apt-get clean and sudo apt-get autoremove" also tried pysochats web resoures keeps returning error in dpkg

---

### Post by Oldsoldier2003 on 2008-06-10
> **hazman said:**
> i been trying all flavours of the buntu's and gone back to ubuntu.but now am stuck with all kde and kcfe stuff and cannot remove.can not even use gdm as apparently its not running. tried "sudo apt-get clean and sudo apt-get autoremove" also tried pysochats web resoures keeps returning error in dpkg

please paste the error here so we can help sort you out.

---

### Post by hazman on 2008-06-10
this is the error it retuns
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
wayne@ubuntu:~$

---

### Post by Oldsoldier2003 on 2008-06-10
> **hazman said:**
> this is the error it retuns
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
wayne@ubuntu:~$

```
sudo dpkg --configure -a
```

---

### Post by hazman on 2008-06-10
done that now what can i try removing kubuntu again

---

### Post by forestpixie on 2008-06-10
which command have you been using from the psychocat site - the aptitude or apt-get , last time I tried aptitude remove it just got rid of the desktop not the installed packages.

Edit if you are using the apt-get method it is important to use the correct command - they are different for hardy, gutsy, feisty

---

### Post by Paqman on 2008-06-10
Also note that the last part of the commands from Psychocats will install a different desktop. If you just want to remove a desktop then remove the && and everything after it.

---

### Post by forestpixie on 2008-06-10
> Also note that the last part of the commands from Psychocats will install a different desktop. If you just want to remove a desktop then remove the && and everything after it.The last part is to put back the ubuntu desktop which is what the op is trying to do.

---

