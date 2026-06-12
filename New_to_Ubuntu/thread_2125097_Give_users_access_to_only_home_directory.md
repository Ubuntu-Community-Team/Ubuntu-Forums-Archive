---
title: "Give users access to only home directory"
date: 2013-03-13
forum: New to Ubuntu
---

### Post by bellygrevios on 2013-03-13
Hi everyone,
I was wondering if there's a way to give users access to only a certain directory (i.e. the home directory as the title says). I'm trying to allow friends to ssh/sftp into the server without allowing them to screw anything up or snoop around. The only access is through SSH/SFTP if that helps. Based on what the internet is saying chroot is the best option(not sure what that really is) but I'm relatively new to linux and am completely confused. If someone could give me a detailed step by step walkthrough on how to implement chroot or some other way to accomplish the same thing it would be great.

Thanks,
Ubuntu Server Edition 12.04 (LTS)

---

### Post by skinnymg1 on 2013-03-13
Create a user account on the server for them and when they ssh into the machine they will have to use their own credentials. As long as you do not grant sudo "root" priveledges to the user you should be fine.

---

### Post by SeijiSensei on 2013-03-13
I would also override the insecure Ubuntu default of having all users be able to browse other users' directories:

```

cd /home
sudo chmod 700 *

```

Now /home/username is only visible to its owner.  To make this the default for all new users, edit /etc/adduser.conf and set "DIR_MODE" to 0700 instead of the 0755 default.

---

### Post by bellygrevios on 2013-03-14
> **SeijiSensei said:**
> I would also override the insecure Ubuntu default of having all users be able to browse other users' directories:

```

cd /home
sudo chmod 700 *

```

Now /home/username is only visible to its owner.  To make this the default for all new users, edit /etc/adduser.conf and set "DIR_MODE" to 0700 instead of the 0755 default.

Thanks for the response but I don't think this will work for my needs. I have many other users with all different levels of access so by using Chmod on everything it would affect my other users.

---

### Post by bellygrevios on 2013-03-14
> **skinnymg1 said:**
> Create a user account on the server for them and when they ssh into the machine they will have to use their own credentials. As long as you do not grant sudo "root" priveledges to the user you should be fine.

I already have the account created and stopped them from using sudo and switching accounts however, I still do have other I don't want to give them access to any other folders that I have made public (I.e. apache web server, DLNA media server, etc) which are public so all other users can access it

---

### Post by Paqman on 2013-03-14
> **bellygrevios said:**
> Thanks for the response but I don't think this will work for my needs. I have many other users with all different levels of access so by using Chmod on everything it would affect my other users.

Each user will still have access to their own home directory, so unless they really, really need to be able to peek in each others' home folders there's no problem.

If you did need some users to be restricted and some not then using permissions is still the way forward. Simply add those users you want to have access to a special group, give that group read access and cut off everybody else. Sorting this kind of stuff is exactly what commands like chmod and the Linux permissions system is for.

---

### Post by sudodus on 2013-03-14
> **Paqman said:**
> Each user will still have access to their own home directory, so unless they really, really need to be able to peek in each others' home folders there's no problem.

If you did need some users to be restricted and some not then using permissions is still the way forward. Simply add those users you want to have access to a special group, give that group read access and cut off everybody else. Sorting this kind of stuff is exactly what commands like chmod and the Linux permissions system is for.
+1
Use the group permissions to allow the priority users to read and run each other's files, but keep the others out.

---

### Post by schragge on 2013-03-14
You may want to know how specific privileges are managed in Ubuntu: [uwiki]Security/Privileges[/uwiki]

---

### Post by bellygrevios on 2013-03-14
> **sudodus said:**
> +1
Use the group permissions to allow the priority users to read and run each other's files, but keep the others out.

My other users need to be able to look in a media directory and other files not under /home (such as /var/www and others. I can't just stop them from accessing every system folder.

---

### Post by coldcritter64 on 2013-03-14
> **bellygrevios said:**
> Thanks for the response but I don't think this will work for my needs. I have many other users with all different levels of access so by using Chmod on everything it would affect my other users.
Then set permissions of 755 for the directories you want left alone (readable to all) and use permissions of 700 on home  folders you don't want as accessible. Accounts set to 700 permisssions are then protected from prying eyes as your opening post indicated you wanted, but are still fully useable to their owner and root too of course, just not other users.
Remove the * (wilcard) in SejiiSenei's post command and replace the actual usernames, one by one, and set the permissions as you indicated you require.

Edit: on rereading Paqman's post, that is a much better way; setting a special group for the permissions handling would allow easier management for new users added what I posted above OP. A much better option really. cheers and good luck.

---

### Post by sudodus on 2013-03-15
> **bellygrevios said:**
> My other users need to be able to look in a media directory and other files not under /home (such as /var/www and others. I can't just stop them from accessing every system folder.

* It is a good idea to ***backup the system before you do this***, because you can easily break the system, if you remove permissions or change ownership on certain files.
--
Yes, this is possible with *Pacman*'s method. Do you need detailed advice?

- create a group and add those with higher permissions into that group. You can give it any name (not yet used), for example 'plus'.
Use ```
users-admin
``` or edit directly the file **[FONT=courier new]/etc/group[/FONT]** if you know what you are doing

- set the permissions of some directories to be only accessible by the user and that group, 750.
```
sudo chmod 750 directory
``` (Use the actual name of the directory to be addressed.)

- set the group ownership of those directories to be 'plus'
```
sudo chgrp plus directory
```

- set the permissions of other directories to be accessible by everybody, 755 (you wrote 'such as /var/www and others')
```
sudo chmod 755 directory
```

- /tmp should always have rwx for everybody, 777, for the system to work properly.

* Check with ```
ls -l
``` in the directory above the one you want to check, that the permissions are what you want.

- You may need to set permissions and ownership of certain files too. Then use the file name(s) instead of a directory name in the chmod and chgrp command lines.

---

### Post by bellygrevios on 2013-03-16
> **coldcritter64 said:**
> Then set permissions of 755 for the directories you want left alone (readable to all) and use permissions of 700 on home  folders you don't want as accessible. Accounts set to 700 permisssions are then protected from prying eyes as your opening post indicated you wanted, but are still fully useable to their owner and root too of course, just not other users.
Remove the * (wilcard) in SejiiSenei's post command and replace the actual usernames, one by one, and set the permissions as you indicated you require.

Edit: on rereading Paqman's post, that is a much better way; setting a special group for the permissions handling would allow easier management for new users added what I posted above OP. A much better option really. cheers and good luck.

So could I just do this to /* because like I said before server stuff isn't under /home. Also what would the consequences of this be on other users?

---

### Post by bab1 on 2013-03-16
> **bellygrevios said:**
> So could I just do this to /* because like I said before server stuff isn't under /home. Also what would the consequences of this be on other users?

There are a couple of points that might consider that haven't been touched upon.

 [LIST]
[*] The permissions of a file system tree (i.e. /etc or /var) are best left alone if you are not comfortable with what is needed by the OS.  
[*] On the other hand you don't need to use /var/www as the web root.  I use Apache and have configured /data/www for all of my web content.
[*] If you have multiple users that are responsible for the web page content then you need to make the group permissions inheritable.  By default, Linux group permissions are NOT inheritable.
[/LIST]

If you do this and set the users /home directory permissions to 0770, the data will be outside of the home directory structure and away from the rest of the OS file structures.  You can set the /data permissions any way you want without interfering with OS or the users normal permissions.

Here is what I do
[LIST=1]
[*] Create the /data/www file structure
[*] Set the folder /data/www group ownership to www-content (a group I created)
[*] Set the permissions on the /data/www to 2770 ( this sets the sgid bit for inheritance)
[*]
[/LIST]
You only need to set the permissions on the folder www in the directory /data.  At this point anything created in that folder by a user in the group www-content will have the ownership of $USER:www-content.  The permissions for a folder will be 775 and the files will be 664, but no user that is not part of the www-content group will be able to descend into the www directory and therefore can't view or change anything in there. 

Others have described how to create user groups and add user to those groups.  None of this will affect normal users or add more than access to /data/www for the users that you do add to the new group you create.

---

### Post by sudodus on 2013-03-16
> **bellygrevios said:**
> So could I just do this to /* because like I said before server stuff isn't under /home. Also what would the consequences of this be on other users?

It is a ***bad idea*** to change permissions or ownership to /*

It might corrupt your system, either break it (so that it won't work, or part of it won't work) or leave it open to attacks (break the security).

You need to be careful with these commands. So read some tutorials on the internet, reread all the advice in this thread, bab1's advice is good, and decide what you want to do!

But don't do it at once! First backup your system. Then make a test directory, and inside it try the commands. Create a subdirectory tree with some files, and use the commands to create the permissions you want, and test with some users, if they get the access they should (no more, no less).

When you get this right, you can do it to the real directories.

---

### Post by coldcritter64 on 2013-03-16
> **bellygrevios said:**
> So could I just do this to /* because like I said before server stuff isn't under /home. Also what would the consequences of this be on other users?
Be careful not to do so to any system folders, folders in the Ownership of a user should be alright to change, if all folders affected by the wildcard (*) are user folders then it should be alright, be careful not to accidently change any "lost+found" or system folders etc **Edit: especially not from /***. However if more users are likely to be added or removed, using the new group suggestion by Paqman would make your job of administering the system easier. 

If the user "owns" the folder you change the permissions on, keeping the "users" permission setting at 7 (777=u,g,o=user,group,others), means no effect to the user. 

By setting a folder's "group" permissions to 0, no user, also a member of this group, can even view it. 

Setting the "others" number to 0 gives same result as for "group" access, ie. none at all, your folder is accessible only to its owner and root, no "group" access or from "others". Different permissions values in conjuction with group access can cater for varying degrees of access control and administration. Cheers.

---

### Post by squakie on 2013-03-17
I suspect you may be looking for a quicker way to do this, such as your request about /*.  As previously mentioned, DO NOT DO THIS!  

System security and access rights are not a simple "do this" process.  You have to look at what you want to do, what actual folders/files are affected, and use a group (or even more than 1) to set who gets access to what, and what that access should be.

For what you are trying to do, it might be best to first map out what folders/files need what type of access for which users.  By mapping this out you'll be able to more clearly see where the groups of the same access needs are - which can give you a hint on a user group to own it and the access rights to be given.

---

