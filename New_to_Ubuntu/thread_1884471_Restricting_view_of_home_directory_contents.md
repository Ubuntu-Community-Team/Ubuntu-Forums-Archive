---
title: "Restricting view of home directory contents"
date: 2011-11-21
forum: New to Ubuntu
---

### Post by whiteleech on 2011-11-21
[FONT=Calibri][SIZE=3]Hi there,[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]I’ve set up numerous user accounts. All the users are restricted to only viewing and editing files in their own directory using the chroot_list. They can however go to /home and using 'ls' can view other usernames/directories. They can’t view the files in the directories but they can see a list of all the other directories/users. How can I prevent this?[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]Cheers[/SIZE][/FONT]

---

### Post by mikewhatever on 2011-11-21
You could chmod the home directories, removing read access from 'other', I suppose.

```
sudo chmod o-r /home/dir_name
```

---

### Post by whiteleech on 2011-11-23
Hi there,
 
Thanks for your reply. I tried that code in root then logged in to one of the user accounts. Typed:
 
cd /home
ls
 
and it still came up with a list of all the other users. Am I doing something wrong or completely missing something?

---

### Post by Lars Noodén on 2011-11-23
For directories, you also need to get rid of the executable bit.  That is what allows name lookup.  This will clear all permissions for non-owners of the home directories:

```

sudo chmod o= /home/*

```

---

### Post by dave0109 on 2011-11-24
To stop the user listing the contents of /home, you'll need to remove the permissions for /home itself.

```

cd /
chmod o= home

```

---

### Post by Lars Noodén on 2011-11-24
> **dave0109 said:**
> To stop the user listing the contents of /home, you'll need to remove the permissions for /home itself.

```

cd /
chmod o= home

```

Clearing all privileges for Other for /home will lock out users.  The directory /home needs at least execute privileges for Other so the users can access their home directories. 

```

sudo chmod o=   /home/*
sudo chmod o=rx /home

```

---

### Post by dave0109 on 2011-11-24
Ah OK, so basically, the OP can't do what he wants to do.

---

### Post by Lars Noodén on 2011-11-24
> **dave0109 said:**
> Ah OK, so basically, the OP can't do what he wants to do.

He can do it.  It's just that the changes must be applied to each user's home directory and /home itself must be left untouched.

---

### Post by dave0109 on 2011-11-24
Maybe I got the wrong end of the stick. I thought he was trying to stop users seeing the other users' directories that are held in /home.

---

### Post by Lars Noodén on 2011-11-25
> **dave0109 said:**
> Maybe I got the wrong end of the stick. I thought he was trying to stop users seeing the other users' directories that are held in /home.

Try it.  You'll see that in order to stop users from seeing other users' home directories, the changes need to be made to the home directories and not /home.

---

### Post by dave0109 on 2011-11-28
I don't need to try it, but maybe you do. :)

With the permissions set as you suggest, the OP will be able to go to /home, do an ls and see all the other users on the system, because they will have their own directories in /home.

But given that the OP seems to have vanished from the thread, I guess we'll never know what it was that he wanted exactly.

---

