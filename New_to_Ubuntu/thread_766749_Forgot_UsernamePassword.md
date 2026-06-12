---
title: "Forgot Username/Password"
date: 2008-04-25
forum: New to Ubuntu
---

### Post by frayalejandro on 2008-04-25
A friend of mine hasn't used Ubuntu for a while, and he forgot his user name and password. Is there a way to log in?

---

### Post by tom56 on 2008-04-25
If there is another user on the computer who has admin rights then they could change your friend's password.

---

### Post by sisco311 on 2008-04-25
Reboot the computer and select Recovery Mode from the Grub menu.
When the computer first starts up, you have a few seconds to push esc to go into GRUB.

When the command prompt appears, issue the command:

```
ls /home
```This command will print the home folders.(home folder name = user name)

Type:

```
passwd username
```to change the password.

```
reboot
```to reboot the computer.

---

### Post by Oldsoldier2003 on 2008-04-25
> **frayalejandro said:**
> A friend of mine hasn't used Ubuntu for a while, and he forgot his user name and password. Is there a way to log in?

reboot the computer and from the grub menu select the option that says (recovery mode) at the end of the decription

Once you are booted up in recover mode type passwd <hisusername> and reset his password.

If he doesn't know his username an easy way to figure it out is ls /home and it will show the directories inside of the home dir. Usually the name of the dirctory is the same as the username.

A slight more accurate way to figure it out is to type ```
cat /etc/passwd
```
he should see some entires that look like this:
```
frank:x:1000:1000:Frank,,,:/home/frank:/bin/sh
```

in this case frank is the first user installed on the system (group 1000 tells us that) so changing franks password and logging in as frank will able us to resolve any further issues we have, unless frank has been removed from the admin group.

to reboot after you made your changes type ```
reboot now
```

---

### Post by frayalejandro on 2008-04-25
Thanks a lot! The information is pretty clear to me. I'll send it to him. We'll see what happens...

:)

---

### Post by frayalejandro on 2008-04-27
Well, my friend seems to have solved his problem, thanks to the information you posted.
Thank you very much.

---

### Post by Oldsoldier2003 on 2008-04-27
you're very welcome, glad we could help

---

