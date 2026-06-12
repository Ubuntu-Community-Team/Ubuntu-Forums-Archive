---
title: "allow two users to read/write files and folders to an specific folder"
date: 2013-01-22
forum: New to Ubuntu
---

### Post by herbert tamayo on 2013-01-22
hi, I want to allow two users to read/write privileges to an specific files and folders, currently the owner of the dir is "user1.user1", so, I add the user "user2" the "user1 group" with this command:

```

nano /etc/group

```

then i tried that the user2 to write files into that directory but it does not work, the error got it was: "permission denied", so my question is:

what command should i use to add permission to user1 and user 2 to read/write files?

regards

---

### Post by audiomick on 2013-01-22
I believe you can use chown for that. You would have to look at the man page
```
man chown
``` for details, as I don't know the exact details.

I usually do that sort of thing via the file manager. If you own the directory, you can right click on it, choose properties and go to the permissions tab. If you don't own it, you can do it with an instance of the file manager with root permissions. You can get this with
```
gksudo nautilus
```

Close that as soon as you are finished. On the one hand, if you do stuff in there, you can end up with files that belong to root, and on the other hand, it will allow you to erase important system files if you tell it to.

EDIT: I just had a look at the man page for chown. Perhaps chmod is a better idea. Look at 
```
man chmod
```

---

### Post by deadflowr on 2013-01-22
Try:

```
sudo adduser username groupname
```

Username being user2 and groupname being the group of user1.
This will add user2 to user1's group.
See:
```
man adduser
```

Then set the permissions with:

```
sudo chmod -R 77X folder
```
This will give both the owner and group users full rights.(The X represents any number between 0 and 7, don't put X it'll probably cause errors.

Sidenote: Editing /etc/group needs root privileges, so just using nano without sudo will result in permission denied.

---

### Post by Vaphell on 2013-01-22
```
sudo chmod -R 77X folder
```
why would you want all files to be executable?

---

