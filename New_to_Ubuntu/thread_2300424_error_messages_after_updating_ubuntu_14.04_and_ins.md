---
title: "error messages after updating ubuntu 14.04 and installing gdm"
date: 2015-10-25
forum: New to Ubuntu
---

### Post by aman_ankit on 2015-10-25
i updated my ubuntu 14.04 installation and couldn't login. after looking through previous posts i managed to install gdm through command line and log in. but i get error messages and my home directory is full of weirdly named files. please help.

---

### Post by Bashing-om on 2015-10-25
aman_ankit; Hi !  My Welcome to the forum .

Let us see what we can do about this .
Boot to the login screen, here activate a console with key combo ctl+alt+F1 ;
Post back - Between code tags - the outputs of terminal commands:
```

ls -al /
ls -al /home
ls -al /home/<user_name>
echo $XAUTHORITY

```
Where in <user_name> is your actual login user ID .
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

Here we look at the permissions set and if "you" are authorized to access your desktop.
Will also give us an indication of where else to look if all here is proper.

[INDENT][INDENT]so the hunt begins
[/INDENT][/INDENT]

---

