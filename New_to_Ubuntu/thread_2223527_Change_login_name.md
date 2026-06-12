---
title: "Change login name"
date: 2014-05-11
forum: New to Ubuntu
---

### Post by ray9 on 2014-05-11
I have tried to solve this using the recovery mode and  another method with no success.  Somehow when I upgraded to Ubuntu 14.04 my user name and password became married together.  <snip>  What it's supposed to be is "ray".  "usermod -l  -m -d /home"  I don't know what names to put where.  Could someone give me the exact command using my supplied information.  "ray" is the user (login) name and "<snip>" is the wrong user login name.  "<snip>" is my password.  So when I go to login it says "ray<sniop>" on top of the password  box when it supposed to say "ray".

Thanks

---

### Post by Elfy on 2014-05-11
I've edited out the password that you told anyone who read the thread. Unless you don't use that as password in which case change it back.

---

### Post by jensmaucher on 2014-05-11
```
usermod -l NEW_NAME OLD_NAME
```

---

### Post by ray9 on 2014-05-12
Thank you.  It says the old name doesn't exist, yet it does.  It shows above the login password box.  Are the underlines needed?

---

### Post by ray9 on 2014-05-12
Solved.  I went to system settings > user accounts> adminstrator and changed  the messed up user name to the user name I wanted  and that did it.

---

### Post by jensmaucher on 2014-05-12
No, the underlines are not needed. Fine that it is solved. Please mark this thread as solved too :)

---

