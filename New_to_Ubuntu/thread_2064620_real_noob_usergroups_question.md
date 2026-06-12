---
title: "real noob user/groups question"
date: 2012-09-29
forum: New to Ubuntu
---

### Post by s1baker on 2012-09-29
hi,
 I am up the only user on my system ( up until a week ago ), and therefore I am the admin with sudo rights.
I have my own home folder. So recently I decided to create another user account for someone, and now 
I have just discovered that they have been wandering around anywhere they want to, into my home folder,the system, etc., you name it,
and look at all the files and read them.
 I don't know much about adding users on my system, but I don't think it's supposed to work that way.
The user is not a member of any group except their own. I thought a new user was supposed to be confined
in their own folder until they were given permission to go to admin allowed places.
 Maybe someone can enlighten me?

---

### Post by Gone fishing on 2012-09-29
Yes you can make it so that only you can see your files you need to change the permissions the easiest way is from the commandline.

sudo chmod -R 700 /home/username

Obviously change username to your username!

chmod is the command for changing permissions, -R is recursive (ie the directory and files subdirectories etc, 7 is full permissions for the user and 0 is no permissions for other users or members of the same group.

---

### Post by s1baker on 2012-09-29
if the user I have added is not a member of my group, should that not allow them to enter my folder?
Also, how do I keep them from going into the system folders and files?

---

### Post by Gone fishing on 2012-09-29
> if the user I have added is not a member of my group, should that not allow them to enter my folder?

Depends on the permissions 755 will allow users in or out of your group to look but not change files, 750 only users in your group could read other users could do nothing.

> Also, how do I keep them from going into the system folders and files? 

They can only see - they can do nothing as personal files (of any kind) are not there it doesn't matter

---

### Post by deadflowr on 2012-09-29
Gone fishing's definitely right. Setting your own home folder permissions to 700 is the best way to restrict access.
As far as changing permissions on system folders and files, don't.
Linux is permission based. Changing permissions on system files can ultimately restrict you ability to access those files, and not just another user. You need access to the files to run any program as a user.
 And besides, since only root can run full rights on system files, accessing those files alone is no harm. Any file/folder which contains vital information, is most likely set with more restrictive permissions(like /etc/shadow).

---

### Post by s1baker on 2012-09-29
I guess I am confused here.

 Suppose I am the owner/adminatrator of this computer. Call me "A"
I have a folder called "A". Now I set up separate accounts for "B", "C",
and "D".
I do not want "B" to access my folder. I have no problem with "C" and "D".
I can't just have a "no read, no edit, no execute" for everybody ( this would exclude "C" and "D" )

what do I do?
Seems like there needs to be some unique setting for "B"

---

### Post by deadflowr on 2012-09-30
You can follow Gone fishing's second post and set the permissions to 750, or even 770 locking out others.
Here's a quick and simple howto for adding users to groups, and adding groups:

[http://www.cyberciti.biz/faq/howto-linux-add-user-to-group/]("http://www.cyberciti.biz/faq/howto-linux-add-user-to-group/")

---

### Post by sisco311 on 2012-09-30
> **s1baker said:**
> I guess I am confused here.

 Suppose I am the owner/adminatrator of this computer. Call me "A"
I have a folder called "A". Now I set up separate accounts for "B", "C",
and "D".
I do not want "B" to access my folder. I have no problem with "C" and "D".
I can't just have a "no read, no edit, no execute" for everybody ( this would exclude "C" and "D" )

what do I do?
Seems like there needs to be some unique setting for "B"

By default, in Ubuntu every user has its own primary group. The name of its primary group is the same as its user name. 

By default, the home directory has 0755 permissions. Read/Write/Execute for user (`A'), read/execute for group (`A') and read/execute for others.

To accomplish what you want, you have to remove read/execute permissions from others. As user `A', run:
```
chmod 0750 "$HOME"
```
As you mentioned this will exclude every other user, but the ones who are members of the group `A'. So, to grant access to the home directory of user `A' for another user, you have to add the user to the group `A':
```
sudo gpasswd -a C A
sudo gpasswd -a D A
```

You can read more about Unix/Linux file permissions here:
[http://content.hccfl.edu/pollock/aunix1/filepermissions.htm](http://content.hccfl.edu/pollock/aunix1/filepermissions.htm)

HTH

---

