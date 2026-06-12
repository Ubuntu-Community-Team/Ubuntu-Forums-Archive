---
title: "Installed Ubuntu, can't remember password or setting one"
date: 2008-07-20
forum: New to Ubuntu
---

### Post by Stephen Reza on 2008-07-20
Stupid question! Just finished installing ubuntu and Im being prompted for username and password. What do I do when I dont know my own password, or remember setting one during the install? Any help would be great!

Thanks!

---

### Post by TSS on 2008-07-20
You need to reboot in recovery mode.  Then, select "drop into root shell" and type:
```
passwd yourUsernameHere
```
Enter in your new password and you are all set.

---

### Post by benfindlay on 2008-07-20
You may have installed the oem version of ubuntu. Try logging in with 'oem' as your username.

Hope this helps!

---

### Post by ibuclaw on 2008-07-20
Boot into recovery mode, select "Root Shell" and run this instead to create and setup a new user.
```
adduser --group --add_extra_groups YOURNAME
```
Fill in your details (Password, etc. You can leave everything but the Password Blank if you wish), then run
```
usermod -a -G admin YOURNAME
```
And all is done!

To test if the new settings have been applied correctly, run
```
groups YOURNAME
```
And you'll get the output:
[B]YOURNAME dialout cdrom floppy audio video plugdev users admin
[/B]

type in
```
exit
```
to leave the shell, and select "Continue with Normal Boot" to continue with the normal startup.

Then login with your new name and password.

[EDIT]
NOTE: replace "YOURNAME" with your own desired username, of course.

Regards
Iain

---

