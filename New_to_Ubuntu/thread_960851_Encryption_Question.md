---
title: "Encryption Question"
date: 2008-10-27
forum: New to Ubuntu
---

### Post by KuroYoma on 2008-10-27
I have a folder that i want to encrypt so that a password have to be entered for anyone to access it.  I have multiple users and i know i can set the permissions on the folder itself but i want to lock the folder so when anyone double clicks on it(even myself) a password has to be entered.  Is this possible?

I am running ubuntu 8.04 with 2.6.26.1 custom kernel

Edit: *Bump*

---

### Post by KuroYoma on 2008-10-27
*Bump*

---

### Post by sayems on 2008-10-27
**[SIZE="4"]_Altering Permission_[/SIZE]**

You can easily change permissions of files and directories by using the "chmod" command, For Example, if you want to change a file so that everyone on the system can read and write to it, type the following:  **sayem:~$ chmod a+rw myfile**

In other words, you're adding read and write (rw) permissions for all users (a), including the owner, the group, and everyboddy else, here's another example:  **sayem:~$ chmod a-w myfile**

This tells Linux that you want to take away (-) the ability of all users (a) to write (w) to the file. However. you want to leave the other permissions as they are..

If you specify u, you can change permissions just for the owner (u is for "user", which is the same as "owner"); [B]sayem:~$ chmod u+rw
[/B]
This will configure the file so that members of the group that owns the file can't read or write to it. Using on o, which is for "others", will configure the file permissions for those who aren't the owner of the file or who are not in the group that owns the file - the last three digits of the permission list.  A typical day-to-day use of chmod is in making a program file that you've downloaded executable. Because of the way the internet works, if you download a program to install on your computer, it can lose its executable status while in transit. In this case, issue the follwing command;  **sayem:~$ chmod u+x myprogram**  This will configre the file so that the owner (u) can execute (x) it.

---

### Post by cariboo on 2008-10-27
Have look here:

[http://www.ubuntugeek.com/crypt-manager-an-encrypted-folder-manager-for-ubuntu-linux.html](http://www.ubuntugeek.com/crypt-manager-an-encrypted-folder-manager-for-ubuntu-linux.html)

It might be what you are looking for.

Jim

---

### Post by DGortze380 on 2008-10-27
> **KuroYoma said:**
> I have a folder that i want to encrypt so that a password have to be entered for anyone to access it.  I have multiple users and i know i can set the permissions on the folder itself but i want to lock the folder so when anyone double clicks on it(even myself) a password has to be entered.  Is this possible?

I am running ubuntu 8.04 with 2.6.26.1 custom kernel

Edit: *Bump*

I don't know how to require a password for a file in ubuntu, but I should point out that this is not necessarily encryption... it's simply requiring a password. Now the password may be a key for some type of encryption, but not necessarily.

---

### Post by nhasian on 2008-10-27
i noticed you are using Intrepid Ibex Ubuntu 8.10.  One of the new features is the private folder for each user.  its not enabled by default but you can enable it by typing in a terminal:

```
sudo apt-get install ecryptfs-utils
ecryptfs-setup-private 
```

---

### Post by KuroYoma on 2008-10-28
I know about file/folder permissions.  The password is what I am looking for.  Actually i said at the top i was running 8.04  Hardy Heron with a my custom made kernel 2.6.26.1

That encryption program looks interesting.  I will have to try that. Thanks

So i am taking it that just adding password requirement on a folder isn't exactly common ground.

---

### Post by KuroYoma on 2008-11-01
So does anyone have any idea how to put a password requirement on a folder.  I have multiple users but i also leave my laptop running and want to block this folder if one of my roommates or one of their friends jumps on it real quick.

---

