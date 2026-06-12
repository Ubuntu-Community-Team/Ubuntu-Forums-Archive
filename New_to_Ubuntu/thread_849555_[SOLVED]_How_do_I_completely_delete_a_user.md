---
title: "[SOLVED] How do I completely delete a user?"
date: 2008-07-04
forum: New to Ubuntu
---

### Post by djvasco on 2008-07-04
Aloha all.  I'm trying to completely delete a user.  Steps done : System=>Administration=>Users and Groups=>Delete (specific user).  Went to groups and also deleted.  When trying to add user back in I get the prompt: **Home directory already exists.  Please enter a different home directory path.**

How do I delete the user from the home directory?  Thanks.

---

### Post by sayakb on 2008-07-04
At a terminal:
```
sudo rm -rf /home/*username_to_remove*
```CAREFUL: Enter the correct username. This command wipes out anything you specify it to.

---

### Post by ibuclaw on 2008-07-04
Remove the folder from the /home directory.

ie:
If the username was "**steve**", Press Alt+F2 and type in
```
gksu nautilus /home
```
in the command box and press Enter.

Then locate and delete/rename the folder entitled "**steve**"
Then promptly close that session of Nautilus and retry again.

[EDIT]
For future references, I personally prefer the swift command
```
sudo deluser --remove-home **username**
```

Regards
Iain

---

### Post by djvasco on 2008-07-04
Thanks, able to remove the file with nautilus.  Mahalo:)

---

