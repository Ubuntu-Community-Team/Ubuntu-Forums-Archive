---
title: "Create user with default values"
date: 2013-10-01
forum: New to Ubuntu
---

### Post by svprdga on 2013-10-01
Hello;

I installed one Ubuntu Server for me to work, and all is all right; but now we have one new worker and I need to create a user to her. I created the user using 'useradd' and setted her the password.

Now, hat new user has some problems in comparisson with my own user (which was created on the system installation), that is:

- No /home folder created.
- No autocomplete files enabled.
- Prompt is empty.
- New files are created using 664 permissions (my users creates the files with 755).
- The console has no colours...(using PuTTY).

So my question is...there is a way to create one user with all that defaults values setted as my user has?

Thanks.

---

### Post by slickymaster on 2013-10-01
You can use the **useradd** command with the -d option to set the home directory for the user. The -m option will force useradd to create the home directory.
```
sudo useradd -d /home/testuser -m testuser
sudo passwd testuser
```
This will create the user named testuser and give him his own home directory in /home/testuser. The files in the new home directory are copied from the /etc/skel folder, which contains default home directory files. If you wanted to set default values for your users, you would do so by modifying or adding files in that directory.

Alternatively there's the **adduser** command which is easier than the useradd command, because it prompts you for each piece of information:```
sudo adduser <username> 
```

EDIT: a good read on the subject - [User Management]("https://help.ubuntu.com/12.04/serverguide/user-management.html")

---

### Post by steeldriver on 2013-10-01
Excellent answer from slickymaster

If the shell is still not behaving as you expect after copying the .bashrc,  .bash_logout, and .profile files  from /etc/skel to the new home directory it may be that 'useradd' has set the default login shell to /bin/sh not /bin/bash. If so your new user can  change that herself (no sudo required) with

```
chsh -s /bin/bash
```

or an admin can do it as

```
sudo chsh -s /bin/bash *username*
```

---

