---
title: "extra ext4 partition"
date: 2022-08-17
forum: New to Ubuntu
---

### Post by arminimra on 2022-08-17
when installing Ubuntu, I created an additional partition in ext4 format for my files (like drives in Windows), after installation, in order to be able to use it, I changed owner from root to my user with the chown command, So far there was no problem, I can use it easily Now I have a problem and that is that standard users can't enter this partition at all, what should I do?

---

### Post by yancek on 2022-08-17
If the users all belong to a specific group, give that group permissions on the mount point directory.  Depends upon what permissions you want these users to have.  Permissions of 755 would give the users read/write/execute permissions. user=7,  group=5,  others=5.  Read = 4, Write = 2, Execute = 1.  More detailed explanation with examples at the link below.

 [https://www.redhat.com/sysadmin/manage-permissions](https://www.redhat.com/sysadmin/manage-permissions)

---

### Post by Dennis N on 2022-08-17
> Now I have a problem and that is that standard users can't enter this partition at all, what should I do?
Right click on the partition's mount directory in Files.
Click on "Properties"
Examine "Permissions" Tab.
For "Others" Access usually is set to "Access Files".

Others = anyone besides the owner of the directory and users in the group

---

### Post by arminimra on 2022-08-17
> **Dennis N said:**
> Right click on the partition's mount directory in Files.
Click on "Properties"
Examine "Permissions" Tab.
For "Others" Access usually is set to "Access Files".

Others = anyone besides the owner of the directory.
All permissions are set to rw

---

### Post by Dennis N on 2022-08-17
> **arminimra said:**
> All permissions are set to rw

Well, just **rw** permissions on a directory does not allow opening it. The execute (x) option needs to be set.
The "Access Files" setting mentioned in my previous post results in **r-x** permissions.

---

### Post by arminimra on 2022-08-18
> **Dennis N said:**
> Well, just **rw** permissions on a directory does not allow opening it. The execute (x) option needs to be set.
The "Access Files" setting mentioned in my previous post results in **r-x** permissions.

solved, it was not related to permissions

---

### Post by ajgreeny on 2022-08-18
So please tell us what the solution was.
It is very helpful to other users who may have similar problems.

Please also mark the thread as SOLVED from the Thread Tools menu up-top.

---

### Post by arminimra on 2022-08-18
The problem was mounting the partition, when we turn on the system, the partition is automatically mounted for the first user who enters the system, if another user wants to use that partition without restarting the system,  First, it should eject the partition through the file manager then mount it again. There is another way to mount the partition for all users.

[SIZE=5]**[B]How to auto-mount partitions on startup using Gnome Disks**[/B][/SIZE]


[SIZE=4]Choose partition - Click the button with the gears icon under it - Click Edit Mount Options - Uncheck user session defaults - Check mount at system start up - **Done**[/SIZE]

---

