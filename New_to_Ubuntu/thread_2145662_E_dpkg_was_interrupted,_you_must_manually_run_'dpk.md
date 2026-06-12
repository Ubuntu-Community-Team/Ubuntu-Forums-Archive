---
title: "E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct"
date: 2013-05-16
forum: New to Ubuntu
---

### Post by mreyna16 on 2013-05-16
ive been getting an error message, and ive googled and have seen that an app manager process is running. ppl seem to report that you have to find what is running, question is, how?

here is the error msg ive been getting:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

---

### Post by mörgæs on 2013-05-16
My guess is that 
> **mreyna16 said:**
> ...you must manually run 'dpkg --configure -a' to correct the problem. 

---

### Post by arpanaut on 2013-05-16
Shut down any package managers that you have open and open a terminal (ctrl+alt+t) and input the command
```
sudo dpkg --configure -a
```enter your user password and see if that corrects things.
If that does not work reboot, then open a terminal and enter the same command and post the result here.

---

### Post by 3rdalbum on 2013-05-16
Can you please confirm that this is your 13.04 machine? Or is it a different computer with an old version of Ubuntu?

The reason I ask is because on 10.04 and above, Ubuntu should tell you to run "sudo dpkg --configure -a", not "dpkg --configure -a".

---

### Post by 3rdalbum on 2013-05-16
Can you please confirm that this is your 13.04 machine? Or is it a different computer with an old version of Ubuntu?

The reason I ask is because on 10.04 and above, Ubuntu should tell you to run "sudo dpkg --configure -a", not "dpkg --configure -a".

---

