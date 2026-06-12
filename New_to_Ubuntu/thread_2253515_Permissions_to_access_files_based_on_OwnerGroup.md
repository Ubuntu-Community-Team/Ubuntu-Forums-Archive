---
title: "Permissions to access files based on Owner/Group"
date: 2014-11-20
forum: New to Ubuntu
---

### Post by mraccine on 2014-11-20
Hi,

Very new to Ubuntu - using version 13.10, which was setup for us by a friend for in-house website testing and file sharing. There are 2 desktops (Windows) connected to the server. Both desktops can access the files, but only one (call it Desktop 1) can edit them.

All the current folders have owner and group set to "mike:mike"
 
If I chmod 777 the folder that contains the files, then both desktops can edit existing files.

If Desktop 1 creates a NEW folder, owner and group are set to "mike:mike", and only Desktop 1 can edit contents.
If Desktop 2 creates a NEW folder, owner and group are set to "nobody:nogroup", and only Desktop 2 can edit contents.

When I reboot my computer, Desktop 1 has to login to the server to access files (I use mike as login). When Desktop 2 reboots, the files can be accessed without logging in.

Not sure how to go about fixing issue.

---

### Post by redmk2 on 2014-11-20
> **mraccine said:**
> Hi,

Very new to Ubuntu - using version 13.10, which was setup for us by a friend for in-house website testing and file sharing. There are 2 desktops (Windows) connected to the server. Both desktops can access the files, but only one (call it Desktop 1) can edit them.

All the current folders have owner and group set to "mike:mike"
 
If I chmod 777 the folder that contains the files, then both desktops can edit existing files.

If Desktop 1 creates a NEW folder, owner and group are set to "mike:mike", and only Desktop 1 can edit contents.
If Desktop 2 creates a NEW folder, owner and group are set to "nobody:nogroup", and only Desktop 2 can edit contents.

When I reboot my computer, Desktop 1 has to login to the server to access files (I use mike as login). When Desktop 2 reboots, the files can be accessed without logging in.

Not sure how to go about fixing issue.

The problem requires several configuration changes.  First you need to use a common group for all users of the directory.  Then the you grant ownership by that common group to the shared directory. Lastly you need to have either the inheritance bit set so or set a default ACL for that group on that directory so that all files and subdirectories created have the common group assigned ownership.

The reason you have users nobody:nogroup is due to Samba's use of nobody:nogroup for all guest users.  You should allow access to the Samba share via valid users in the common group (e.g.  valid users = @users (where users is the name of the common group)).  This way you will also know who created the files as the user will be the creator.  If I created a file it would have ownership like this: red:users.  If you created a file it would have ownership like this: mike:users.

Are you the administrator for the Ubuntu host?  This version of Ubuntu is [EOL]("http://fridge.ubuntu.com/2014/07/17/ubuntu-13-10-saucy-salamander-end-of-life-reached-on-july-17-2014/") as of July 2014.  You should look into upgrading Ubuntu 14.04 LTS so you have 5 years of updates.  Did you also help set up the Samba share?

---

### Post by Habitual on 2014-11-20
> **mraccine said:**
> If I chmod 777 the folder that contains the files, then both desktops can edit existing files. As a gentle nudge in the kung.fu that is Linux Permissions, this is a very bad habit and it really doesn't "fix" anything.

[ Create a group. ]("http://manpages.ubuntu.com/manpages/trusty/man8/groupadd.8.html")
add both users to the group
```
chgrp -R <group> /path/to/directory
```
and maybe a
```
chmod g+w /path/to/directory
``` is likely necessary also.

[http://www.washington.edu/computing/unix/permissions.html](http://www.washington.edu/computing/unix/permissions.html)
[http://askubuntu.com/questions/124246/what-command-changes-the-group-setting-for-a-directory](http://askubuntu.com/questions/124246/what-command-changes-the-group-setting-for-a-directory)

Have a Great Day and Be Safe!

Sorry, hindsight editing now I "see" samba. Well... [https://www.samba.org/samba/docs/using_samba/ch09.html](https://www.samba.org/samba/docs/using_samba/ch09.html)

---

### Post by mraccine on 2014-11-20
Thanks for the responses.

I understand the process so far of adding users to the group, but what is the name I would add to the group for the second desktop? In other words what is the users name?

---

### Post by redmk2 on 2014-11-20
> **mraccine said:**
> Thanks for the responses.

I understand the process so far of adding users to the group, but what is the name I would add to the group for the second desktop? In other words what is the users name?

Desktops are not users.  The users logged in to second desktop (or for that matter the first desktop) are what you add to the group.  In other words you do not add machines (hosts).

[COLOR="#0000FF"]Edit:  My guess is that you don't have a specific account for users on desktop2.  Therefore you end up with guest users (nobody) on the server.[/COLOR]

[COLOR="#006400"]Edit2: The users should have accounts on both the Windows clients and the Ubuntu server (both Linux and Samba).  The usernames should be the same on both the server and clients.[/COLOR]

---

### Post by mraccine on 2014-11-20
> 
[COLOR=#006400]Edit2: The users should have accounts on both the Windows clients and the Ubuntu server (both Linux and Samba). The usernames should be the same on both the server and clients.
[/COLOR][COLOR=#006400]

I guess that is the part I don't understand. When desktop 1 prompts for a username I enter mike and the password to the server.
When desktop 2 tries to access the server, she doesn't need a username or password. So desktop 2 is logged in as nobody. How does desktop 2 set up her computer so it asks for a login to the server?[/COLOR]

---

### Post by redmk2 on 2014-11-20
> **mraccine said:**
> [COLOR=#006400]

I guess that is the part I don't understand. When desktop 1 prompts for a username I enter mike and the password to the server.
When desktop 2 tries to access the server, she doesn't need a username or password. So desktop 2 is logged in as nobody. How does desktop 2 set up her computer so it asks for a login to the server?[/COLOR]

You do that at the Samba server configuration.  The file is /etc/samba/smb.conf.  Post the content here and I will show you how to set up the share.  Are you logged into the Windows machine as *mike*?

---

### Post by mraccine on 2014-11-21
[COLOR=#111111][FONT=Arial]Here is the Share section of the smb.conf file - Do you need to see more than the Share section? I've recently changed the create mask and directory mask from 0755 to 0777 (didn't help).
[share]
comment = Ubuntu2 File Server Share
path = /var/www
guest ok = yes
browseable = yes
create mask = 0777
directory mask = 0777
[/FONT][/COLOR][COLOR=#111111][FONT=Arial]read only = no[/FONT][/COLOR][COLOR=#111111][FONT=Arial]
writable = yes[/FONT][/COLOR]

Yes, I'm logged into the windows machine as mike. When I restart my computer, it always asks me to enter credentials to access the folder (mapped as U:). Desktop 2 is never asked to enter credentials.

---

### Post by mraccine on 2014-11-21
Solved!

Thanks Red - when you asked if I was logged into my Windows machine as mike (which I was), it always prompted me to log into the server. The server must read my Windows machine as "mike" which would prompt for a login since 'mike" is the name/administrator of the server. 

When the prompt came up to log into the server this time, I just typed a fictitious name and password - which logged me as nobody:nogroup. Now both desktops can create/edit each other's files and folders.  I did change (chown) all the existing files and folders to nobody:nogroup.

---

### Post by redmk2 on 2014-11-21
> **mraccine said:**
> Solved!

Thanks Red - when you asked if I was logged into my Windows machine as mike (which I was), it always prompted me to log into the server. The server must read my Windows machine as "mike" which would prompt for a login since 'mike" is the name/administrator of the server. 

When the prompt came up to log into the server this time, I just typed a fictitious name and password - which logged me as nobody:nogroup. Now both desktops can create/edit each other's files and folders.  I did change (chown) all the existing files and folders to nobody:nogroup.
If it works for you it works for me!  :-)

---

