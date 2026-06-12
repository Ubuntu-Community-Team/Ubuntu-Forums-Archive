---
title: "Change permissions on all folders and files"
date: 2013-04-12
forum: New to Ubuntu
---

### Post by MohamedBadawy on 2013-04-12
[COLOR=#333333][FONT=Ubuntu Beta]I have ubuntu 12.04 and I have two questions, the first i want to Change permissions on all folders and

 files At the same time where any one can modify or remove it.

The second question the system take along time to boot (open) any ideas for it ?


[/FONT][/COLOR]

---

### Post by Frogs Hair on 2013-04-12
Here is some information to start with while waiting for someone more familiar with changing large numbers of files.  [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

---

### Post by slickymaster on 2013-04-12
It is very important that you realize that in Ubuntu, by default, root has the complete privileges on all the folders and the disk partitions. User account has limited permissions, but the user that installs Ubuntu (you) is automatically added to a group that has permissions to CALL the root user.

[SIZE=3]You must keep in mind that it's very dangerous to play with the permissions of the files and/or folders.
[/SIZE]

---

### Post by Impavidus on 2013-04-12
Changing the permissions of certain system files will immediately break your system, changing the permissions of the others will make it very likely you'll break your system accidentally later. Delete one file you don't know what it's supposed to do and after the next automatic update your computer won't boot. Those permissions are the reason why Linux tends to be a secure system. We're not supposed to help you circumvent that security. And do you really need to change your system configuration every day?

Oh, let me phrase it the kind way: Many newcomers to Linux and Ubuntu think: `Ow, what are those authorisations annoying. I have to type my password for everything. Can't you disable it?´ Well, in principle you can, but it's better not to do so. You see, these file permissions are at the very heart of the Linux security model. They are there to make sure any hacker or any malware that gets in via a security leak in an application or via the account of an unprivileged user with a weak password (you, as administrator of your computer, may have chosen a strong password, but your father or little sister (I've no idea who else uses your computer) may have a very weak one) still cannot modify any important parts of the system. Be rest assured: as soon as you've properly set up your system you'll need to edit those system files almost never. You just need your password less than once a week to install a new package or a kernel update.

Concerning your long boot time: What is long and what are your specs? Ubuntu version, CPU, RAM, type and speed of hard disk, any other information you think may help us.

---

