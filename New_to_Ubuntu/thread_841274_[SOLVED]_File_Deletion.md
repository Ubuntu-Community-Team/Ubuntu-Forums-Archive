---
title: "[SOLVED] File Deletion"
date: 2008-06-26
forum: New to Ubuntu
---

### Post by dinomite89 on 2008-06-26
Hey,

Ive got a file on my desktop that i want to get rid of (its a modem driver that didnt work) but it has a padlock on it and when i try to delete it ({shift} + {Del}) it comes up with an error,

"Error removing file: Permission denied"

any ideas on how tog et permission?

Out.

---

### Post by flytripper on 2008-06-26
open a terminal and cd to Desktop

then:

sudo rm nameoffile

---

### Post by dinomite89 on 2008-06-26
Okay should have mentioned in first post, because i lied, its actually a folder and when i did that last command it errored because it wouldn't let me delete a directory

Out.

---

### Post by flytripper on 2008-06-26
add -r the the line at the end

---

### Post by issih on 2008-06-26
There are options here, but the nicest for a new user is probably to hit alt+F2, then run:

"gksudo nautilus"

that will open a file browser with root priveleges. Just make sure you close it as soon as you are finished deleting your rogue folder, or you will have the ability to wreak havoc :)

Hope that helps

EDIT...in order to actually be useful and help you learn how things work..

in the command line, "rm" is the remove command.

by default it will only delete files not directories as you found.

Using "rm -r" tells remove to drill down into directories and delete files in there too (the -r stands for recursive).

In both of these cases, the command will only let you delete files you have permission to delete, which is what caused your initial problem. In order to rectify this you need to have root (or administrator) privileges. This is achieved with the sudo command. sudo stands for super user do, and basically says run the following command as root.

So "sudo rm" will delete files as the root user. Because being root allows you to do ANYTHING to your computer (including break it irreversibly) the system asks you to enter your login password every time you use sudo, just to ensure you know what you are doing, and give you a chance to back out.

gksudo is exactly like sudo, but intended for use with graphical rather than command line applications. so "gksudo nautilus" launches the nautilus file manager with root privileges.

---

### Post by Ryadt on 2008-06-26
use this carefully
open terminal and type
> sudo rm -rf (name of file)

---

### Post by flytripper on 2008-06-26
thanks for the gksudo nautilus command.. helped me share out a ntfs drive..for general usage on my network.. was looking to do that :)

---

### Post by dinomite89 on 2008-06-26
Thanks, all Fix

Out.

---

