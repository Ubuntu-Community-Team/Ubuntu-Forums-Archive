---
title: "Default password for terminal su command"
date: 2008-10-19
forum: New to Ubuntu
---

### Post by winx on 2008-10-19
Hi 

I,m Joe and new to the forum.

Does anyone know the default password to get to the root. I have a user pass, I don't remember the install asking for a administor password. I don't want to reinstall to fix a simple thing.

---

### Post by DGortze380 on 2008-10-19
> **winx said:**
> Hi 

I,m Joe and new to the forum.

Does anyone know the default password to get to the root. I have a user pass, I don't remember the install asking for a administor password. I don't want to reinstall to fix a simple thing.

Ubuntu does not activate the root account by default. They recommend you do not use the root account at all. I disagree, but am unable to tell you how to activate it on the forum. A quick google search will turn up one of the tens of ways to do it though. ;)

---

### Post by drowner on 2008-10-19
> **winx said:**
> Hi 

I,m Joe and new to the forum.

Does anyone know the default password to get to the root. I have a user pass, I don't remember the install asking for a administor password. I don't want to reinstall to fix a simple thing.

Hi there.

You should not have to enable the Root password.

All the root acces you will need should be obtainable with the Sudo command.

The first user account made is by default the administrator.

BEFORE you think about enabling the root password, read this [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo) 

and try using Sudo

---

### Post by jerome1232 on 2008-10-19
> **drowner said:**
> Hi there.

You should not have to enable the Root password.

All the root acces you will need should be obtainable with the Sudo command.

The first user account made is by default the administrator.

BEFORE you think about enabling the root password, read this [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo) 

and try using Sudo

+1

Not to mention enabling the root account is strongly discouraged and not supported on these forums. That poster shouldn't have given that info on enabling it.

If you are ever following guides and they are telling you to do something as root, just put sudo before the command and authenticate with your own password. To obtain a root shell you can use sudo -i, exit closes the root shell.

---

### Post by overdrank on 2008-10-19
Thread closed as the op has been given the right information. 
[http://ubuntuforums.org/showthread.php?t=765414](http://ubuntuforums.org/showthread.php?t=765414)
Forum policy on log-in-as-root tutorials

---

