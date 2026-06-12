---
title: "Share a dir between users"
date: 2008-11-04
forum: New to Ubuntu
---

### Post by mkoonstra on 2008-11-04
I want a directory to be shared between two users, the directory should be fully accesable to both users and one user may delete the other user files and folders. Furthermore, no other users should be able to have any acces acces to this directory. How do I set this up?

I have made a group which both users are members of. I have made the dir owned by root and that group and give it permissions 770. This works, as either user can create files and folders. However one user cannot delete the other users files/folders, how can I make this possible?

---

### Post by Ek0nomik on 2008-11-04
Wouldn't you need two groups?  One group which can create and delete files, and another group which can only create?

---

### Post by Coreigh on 2008-11-04
Well... no, wouldn't you just need to have both users assigned to one group that has full or write/delete permission?

UPDATE:

create a group named FileShare (or whatever you like)
Add the user to the group (in the same dialog)

Go to the designated shared folder and assign the new group as owner of the folder.

There are GUI and cmdln methods to do this.

[http://ubuntuguide.org/wiki/Ubuntu]("http://ubuntuguide.org/wiki/Ubuntu")

Further update:
Don't use one of the user's default home folders. Create a new folder in /home or /temp
```
sudo mkdir /home/shared
sudo chgrp *groupname* /home/shared
```

---

### Post by milosz.galazka on 2008-11-04
Problem is little more complicated because users create files/directories with their default groups.

You need to look at  access control lists.
Commands: getfacl to see permissions, setfacl to set them....

----
Dirty check:
1007 - group myusers (contains both users milosz, dagmara)
o - shared directory
```
setfacl -m default:g:1007:rwx,u:milosz:rwx,u:dagmara:rwx o/
```

I used /home/o directory.

Also maybe you want to look at *umask* command.

---

### Post by Tallwood on 2008-11-04
Like stated above, when a user creates a new file, it is created within that users default group, no matter what group the directory is assigned to.
You could make both users members of one anothers default groups.

---

### Post by philinux on 2008-11-04
Seems like this has cropped up before.
[http://ubuntuforums.org/showthread.php?t=350067](http://ubuntuforums.org/showthread.php?t=350067)

---

### Post by mkoonstra on 2008-11-04
I found out that setting group id on the folder overrides the behavior that the file is created with the user default group, it inherits the group owners rights. However, the files are created with rights 755, which still means you can only read.

---

### Post by milosz.galazka on 2008-11-04
> **mkoonstra said:**
> I found out that setting group id on the folder overrides the behavior that the file is created with the user default group, it inherits the group owners rights. However, the files are created with rights 755, which still means you can only read.

[http://en.wikipedia.org/wiki/Umask](http://en.wikipedia.org/wiki/Umask)

---

### Post by mkoonstra on 2008-11-04
umask is not on a per directory basis. And it does not stick between sessions?

---

### Post by milosz.galazka on 2008-11-04
> **mkoonstra said:**
> umask is not on a per directory basis. And it does not stick between sessions?

You can set umask in user startup script (~/.bashrc).
All new files/directories will get new permissions.

Did you tried solution using access control lists?

---

### Post by Coreigh on 2008-11-04
If I have two users; Sam and Ralph, and Sam and Ralph both are members of the group called sharefiles, and I change the group ownership of the folder /home/ourdocs to sharefiles ```
 sudo chgrp sharefile.sharefiles /home/ourdocs 
``` and the permissions to drwxrwxr-- ```
 sudo chmod 774 /home/ourdocs 
```

Then both users will not have access to write delete files in that folder?

Or is what I am not getting that when Sam creates a file it is owned by Sam so Ralph can not modify it?

---

### Post by mkoonstra on 2008-11-04
Yes Coreigh, you hit the spot, you cannot edit the other users files.

I think I will change the default umask to 007. Which will give the group write permissions by default. In most cases the group is the same as the user itself so it will not make a difference. The using set group id on a dir finishes it. The files will be created with the right group and permissions.

---

### Post by bodhi.zazen on 2008-11-04
[http://hep.pa.msu.edu/user/groups.html](http://hep.pa.msu.edu/user/groups.html)

Set Group ID : chmod g+s dirname

OR (ACL works better)

ACL : [http://ubuntuforums.org/showthread.php?t=145741](http://ubuntuforums.org/showthread.php?t=145741)

---

### Post by mkoonstra on 2008-11-04
According to this post [http://ubuntuforums.org/showpost.php?p=1193555&postcount=13](http://ubuntuforums.org/showpost.php?p=1193555&postcount=13) is acl the only solution. I will try that. As that way the rights can be inherited.

---

