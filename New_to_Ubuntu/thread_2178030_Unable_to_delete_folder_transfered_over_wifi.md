---
title: "Unable to delete folder transfered over wifi"
date: 2013-10-01
forum: New to Ubuntu
---

### Post by peter_f_calder on 2013-10-01
HI All

I recently transfered some folders from my laptop to my desktop using wifi. I now want to delete them but the folders have a lock on them stopping me. If i go to the properties of each folder and go to permissions at the bottom of the properties it says You are not the owner, so you cannot change these permissions.

Thanks for taking the time to read my post.

Peter

---

### Post by DuckHook on 2013-10-01
Hi peter and welcome to Ubuntu and the forums.

Because Linux is far more secure than Windows, it imposes some security contraints that you may find inconvenient until you get used to them. However, once you get used to them, you will find that they are indispensible to good security and the reason that Linux doesn't need antivirus. One of these security measures is file ownership and permissions, which is what you are dealing with.

Your current issue is easy to explain and is due to the fact that you created files in your laptop as a different user than you log in as in your desktop. When you transfer these files, the ownership and permission info gets transferred along with them. Indeed, they are a part of each file itself. You have two choices:

1. You can set up all your computers so that the login credentials are exactly the same. This is what I do with my various computers. The first user on each computer is DuckHook. Therefore, each computer assigns DuckHook the same UID number and I can transfer any file created in one machine to another with no ownership or permission mismatches.
2. You can change either or both of the owner or permissions on the transferred files so that they can be opened in your destination machine. You do this by opening nautilus as root which will allow you to change the owner and/or permissions freely.```
gksudo nautilus
```You should now be able to change anything you like. **WARNING** You must be extremely careful running Nautilus as root. It allows you to completely hose your system if you are careless because you can delete anything, including critical system files.

Option 1 above is a more involved procedure but it solves your problem in the long term. Option 2 is the quicker option for now, but it must be done every time you transfer a file.

---

### Post by Bucky Ball on 2013-10-01
Welcome ... and if using option 2, as DuckHook suggests, once you have changed permission on those files, *close the window immediately*. You _do not_ want to fool around in nautilus as root. Do what you need to do and leave. ;)

You can also change the permissions using code in a terminal, but bit more involved. If that does tickle your fancy (or for future reference and learning purposes):

[https://help.ubuntu.com/community/FilePermissions#Changing_the_File_Owner_and_Group](https://help.ubuntu.com/community/FilePermissions#Changing_the_File_Owner_and_Group)

;)

---

