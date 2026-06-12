---
title: "[SOLVED] Upgraded, buy keeping home partition.  How do I access my pervious desktops?"
date: 2008-07-26
forum: New to Ubuntu
---

### Post by gloxer54 on 2008-07-26
[SIZE="4"][/SIZE]  I did a clean install from 7.04 to 8.04 still keeping my /home partition.  Now I can not login to any of the previous desktops(for grandkids, ect).  Any ideas how to make that happen?  I mean to be able to log on to any of those other desktops?  My /home folder still shows everything there.  So that is not a problem.  Any help please?  
    Mike

---

### Post by spiderbatdad on 2008-07-26
not sure about the question. Do you mean other user accounts? You can see what user accounts are available through the file browser in the folder /home. If you only see one user account, then that is the only account saved. If there are others, then they can be accessed at log in or through System>>Administration>>Users and Groups.

---

### Post by gloxer54 on 2008-07-26
[FONT="Arial Black"][SIZE="4"][/SIZE][/FONT]  I have tried to log on using one of the other login names and password, but it is as if it was not there.  I guess I need to know how to make it see the accounts in the /home partition and then login.  
  Mike

---

### Post by louieb on 2008-07-26
> **gloxer54 said:**
>  ...but it is as if it was not there.  I guess I need to know how to make...
Since you did a clean install. You will have to add each user back.
As spiderbatdad points out System>Adminstration>Users and groups.

You need to know 2 things about each user.

[LIST]
[*]The Username (login id) ie. joe sam
[*]and the User ID - a 4 diget number. Ubuntu gives the 1st user and ID of 1000 each use after that the # number goes up by 1.
[/LIST]
The user name can be found by looking at the directories in /home.
The numeric user id - I don't know where that can be found. But for future reference /etc/passwd contains both the username and his user id.

The best thing you can hope for is someone will know how to get the numeric user id out of one of the files in his home directory. 
BTW the numeric user id is set in the Advanced TAB of User Settings.

Or if you can remember the order you added users the 1st time if you add them back in the same order all should be well.
Good Luck.

---

### Post by Yannick Le Saint kyncani on 2008-07-26
You can get user and group number with ls -ln. Open a console, go to /home ("cd /home") and list user directories ("ls -ln").

Example with a tmp directory :
drwx------  2 1000 1000   48 2008-07-25 12:52 tmp
The first 1000 is the user number uid, the second 1000 is the group number gid.

Hope it helps

---

### Post by gloxer54 on 2008-08-05
**[SIZE="4"][/SIZE]**  Okay, thanks to Yannick Le Saint kyncani I found the info I needed.  Then I poked around on the forum here and found this command to use in the / partition: "sudo userconfig" .  After using that I then was able to reset the "users" .  I then went to system>administration>users and groups and reset the passwords to what they were before.  Then all went back to "normal.  Thanks people for the help.

---

