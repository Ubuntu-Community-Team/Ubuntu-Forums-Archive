---
title: "Is there a default number of groups in ubuntu"
date: 2013-09-15
forum: New to Ubuntu
---

### Post by emerson1979 on 2013-09-15
Hello
           Does ubuntu have a certain number of groups built in to it? Such as admin group

Thank You

---

### Post by whitesmith on 2013-09-15
I know of only one default group: that of a user's name. During initial configuration an Ubuntu desktop installation prompts for a user name. If the user-to-be picks joe a default group called joe will be system-created. Admin groups don't exist here. Those are a Windows concept. Permissions control access in *nix.

---

### Post by newb85 on 2013-09-16
I don't think that's entirely true.  Running the command 
```
id
```
will show all groups that the current user is a part of.  This will include the one mentioned by whitesmith, the one named after the user.  If the user is an administrator, it will also include "adm".  If the user has sudo privileges, it will include "sudo".  If the user doesn't need a password to log in, it will include "nopasswdlogin".  There are groups for access to some drives.  The list goes on...

---

### Post by deadflowr on 2013-09-16
```
cat /etc/group
```

Pretty much everything before GID 1000(Which should be the first user made's group) should be part of the default groups for your installation. 
You might add a group here or there for some programs that create ones.(I think postfix does this)

---

