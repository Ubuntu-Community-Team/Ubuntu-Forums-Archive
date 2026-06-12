---
title: "Please explain about the user in ubuntu.."
date: 2012-12-06
forum: New to Ubuntu
---

### Post by arunkumargoge on 2012-12-06
who is root,home and who are the user ?..I'm really much confused .. i'm new to ubuntu and i always work with windows..help me please

---

### Post by vanadium on 2012-12-06
It works pretty much the same as current Windows versions.

Different users can have an account. Each user has his place in a directory under /home. Path of the user's home directory is /home/$USER (change "$USER" by your actual login name).

The very first user has administrator (=root) privileges: he has the power to do systemwide configuration. Other users can also be given these privileges, if needed. To perform administrative tasks, e.g. software update or installation of programs using software centre, you have to provide your user password to show that it is still you sitting at the keyboard.

Ubuntu does NOT work with a separate "root" user: the root account is disabled.

---

### Post by lisati on 2012-12-06
The word "root" has several related meanings in Ubuntu. 

If you imagine the file system as a tree, with directories (folders) as the branches, then the "root" directory roughly corresponds to the top-level directory, e.g. "C:\", in Windows. "root" can also refer to the "superuser" whose role is equivalent to the system administrator in Windows.

Linux, as is the case with Windows, allows for more than one person to be allowed to use the computer. Each user of the computer is assigned their own area of the hard disk known as their "home folder", roughly corresponding to "My Documents" in Windows.

Hope this helps.

---

### Post by zombifier25 on 2012-12-06
The Root account is the superuser (think Administrator on Windows). It can do anything and everything, so it's used to do administrative tasks. By default, root it disabled because it's very dangerous left enabled, but you can temporarily run a command as root in order to deal with the system using the "sudo" command. More info [here](https://help.ubuntu.com/community/RootSudo).

Home is the personal folder of a certain user, which contains personal files, configs, etc that belongs to that user (think My Document). The users are the accounts on the system (think.... users on Windows systems?) , which include you.

---

### Post by arunkumargoge on 2012-12-06
It means any user can be a super user if they have password ?

---

### Post by zombifier25 on 2012-12-06
> **arunkumargoge said:**
> It means any user can be a super user if they have password ?

Password to what? If to the superuser, then the superuser is disabled by default in Ubuntu, so there's no password.

If password to their own account, then it depends whether that user has admin rights (more specificly, the rights to run a command as root) If he/she does, then he/she may authenticate to escalate to root to do system work, but only temporarily. This is to prevent a user from accidentally messing up the system, as opposed to *logging as root completely*, in which everything you do can modify the system, and potentially destroying it. The link I posted has more info than I can give here.

---

### Post by vanadium on 2012-12-06
> **arunkumargoge said:**
> It means any user can be a super user if they have password ?

Yes, but an existing administrator of the system has to grant this permission. So as an administrator, you'd only grant such permission if the necessity arrizes and the user can be trusted.

---

### Post by lisati on 2012-12-06
> **arunkumargoge said:**
> It means any user can be a super user if they have password ?

Not all users are created equal. As mentioned earlier in the thread, the "standard" superuser *root* has had its password disabled by default in Ubuntu. To deal with occasions when superuser privileges are required, we have "administrator" users who can use the "sudo" command to temporarily give themselves superuser privileges. More information can be found here: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by AstroLlama on 2012-12-06
The root user, also called the super user, or administrator has access to everything on the computer and can run any command. that users directory is found at /root

Everybody else who uses the computer has to have their own username to log in with. Each user only has access to their own files, found at /home/[username] and cannot create, delete or modify anybody else's files without permission from the Admin.

Typically, the first user created during install will have admin priviliges, meaning they can run administrator commands and make changes to the system if they enter their password. (root user doesn't have to enter the password to make changes). 

in the terminal starting a line with "sudo" allows you to give your personal password and execute a command as the superuser. This is only possible if their username is in the list of sudoers, again the first user created is automatically added to this list.

---

### Post by grahammechanical on 2012-12-06
The official documentation might be more helpful.

[https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

If I did not already know this I would be confused even more by the posts above. Sorry. :)

Regards.

---

