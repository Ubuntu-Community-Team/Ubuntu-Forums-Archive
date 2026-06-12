---
title: "How do I set permissions to copy files?"
date: 2008-06-13
forum: New to Ubuntu
---

### Post by Binary.tobis on 2008-06-13
I downloaded some themes and I am trying to add them to the themes folder, but the folder won't let me copy a files to it. I think it has something to do with permissions, but I'm not sure how to make that work. How do I let xubuntu know that I have the permissions to edit the contents?

---

### Post by KingTermite on 2008-06-13
use "sudo" in front of your copy command. It's in a directory you need sudo privileges to copy to.

---

### Post by sam_delta on 2008-06-13
alt-f2 and type ```
gksudo thunar
``` youll have to type your password and a file manager with full permissions will open

watch your hand as having full permissions you also have the power to mess up your system files

sam

---

### Post by OffAxis on 2008-06-13
you can modify the permissions on the folder you're copying into or you can modify the permissions of the files (to match the folder).
OR
you can just do it as admin
```

cd /folder/files
sudo cp filename /path/to/folder
```

to show the permissions of a folder or file you would use
```
ls -l
```

to change the permissions you would use
```
sudo chown username:groupname filename
```

sudo = super user
chown = change ownership
username = the user you want to own it
groupname = the group you want to own it
filename = the file

you can leave off either the username or groupname so
```
sudo chown :groupname filename
```
would just change the ownership of the group.

---

