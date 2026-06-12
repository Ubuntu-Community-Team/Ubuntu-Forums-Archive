---
title: "Delete a user account???"
date: 2012-06-02
forum: New to Ubuntu
---

### Post by raz7588 on 2012-06-02
ok so i am trying to delete an account from ubuntu 12.04 cinnamon, i am new to using ubuntu, however when i try and delete one of the user accounts it keeps coming up with error messages, i have logged in and changed to login without password on the account but that does not change and still asks for password the error messgae i get is as follows 

GDBus.Error:org.freedesktop.Accounts.Error.Failed: running '/usr/sbin/userdel' failed: /usr/sbin/userdel returned an error (1): userdel: cannot lock /etc/passwd; try again later.

Any help would be great, thank you

---

### Post by inashdeen on 2012-06-02
wait, cinnamon? do you still have your unity on? have you tried deleting the account on Unity?

---

### Post by Silent Warrior on 2012-06-02
raz: I'm not sure I understand what's going on (and, to be honest, I'm not sure you do, either), but I'll try.

Cinnamon is made of awesome, but you're still using the GNOME Control Center (GNOMECC) for user management.
Log in as a different user than the one you want to remove.
Open GNOMECC and look for User Accounts under System.
Because you're performing an administrative task, you'll have to unlock it by entering your root/administrator's password.
Select the user you want to remove and click the minus ( '-' ) button below the pane.

After this, I have no idea what needs to be done, but this should be all the necessary steps.

---

### Post by codemaniac on 2012-06-02
Have you tried the **userdel **command for the user deletion ?
Open a terminal and 
```
userdel *userName*
```

---

