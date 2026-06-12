---
title: "Help adding a new user"
date: 2012-04-18
forum: New to Ubuntu
---

### Post by Scott216 on 2012-04-18
I just setup ubunto 9.04 (I know it's, old, but everything newer runs very very slow on my PC).  I have a 2nd hard drive I want to use for FTP files (for my security camera to write too).  I want to create another user just for the camera's FTP login.  I opened the Users and Groups application and added a desktop user, I change the home directory to the 2nd hard drive.  As a test I logged out and tried to log in as the new user, but I couldn't log in.  So I logged back in as me and went back to Users and Groups.  The new user I setup does not show up in the list of users, but if I try to add that user again, I get an error saying that username already exists.

BTW, I'm using vsftpd.

---

### Post by codemaniac on 2012-04-19
It would be better if you opted for a newer and stable version for Ubuntu , like Ubuntu 11.10 .
Few things you need to check .Just grep your newly created user name in the /etc/passwd file .

```
grep 'your_user_name' /etc/passwd
```

Also make sure the second hdd which hosts your user /home is correctly mounted at startup .

---

### Post by Scott216 on 2012-04-19
When I do a the grep, nothing happens, I just get a command prompt.  So I tried it with my username and I get:
SRG Bldg,,,:/home/srg:/bin/bash

When I created the new user, and set the directory to be /media/ftpdrive/camera1, ubuntu did not create any new directories.  Also, I think I had both the user and home directory named the same, camera1.  Would that cause problems.

---

### Post by Scott216 on 2012-04-19
> **codemaniac said:**
> 
Also make sure the second hdd which hosts your user /home is correctly mounted at startup .


I'm not positive what correctly mounted at start up is, but here's what I tried: 
I rebooted and went to Places menu and I could see an icon for ftpdrive, when I hovered the mouse over it, it said "mount ftpdrive" (which seems to me it's not mounted yet).  I opened File Browser and clicked on ftp drive.  Then I want back to Places menu and hovered over the icon again and it just said "ftpdrive", it didn't say "mount ftpdrive" anymore.  Also in File Browser, it now has the eject icon.

---

### Post by codemaniac on 2012-04-19
> **Scott216 said:**
> When I do a the grep, nothing happens, I just get a command prompt.  So I tried it with my username and I get:
SRG Bldg,,,:/home/srg:/bin/bash

When I created the new user, and set the directory to be /media/ftpdrive/camera1, ubuntu did not create any new directories.  Also, I think I had both the user and home directory named the same, camera1.  Would that cause problems.

Sorry i cannot get you .Did your new user has its entry in /etc/passwd ?
If your new user is created properly then it must have an entry in the above file .
Login with your new user and see what its home is and post .
```
echo $HOME
```

---

### Post by codemaniac on 2012-04-19
One thing also please note that if your new user is not created or configured properly , you may consider deleting and recreating it (take backup of $HOME if necessary) .deluser command with --remove-home option will delete the user and its home directory .

---

### Post by codemaniac on 2012-04-19
> **Scott216 said:**
> I'm not positive what correctly mounted at start up is, but here's what I tried: 
I rebooted and went to Places menu and I could see an icon for ftpdrive, when I hovered the mouse over it, it said "mount ftpdrive" (which seems to me it's not mounted yet).  I opened File Browser and clicked on ftp drive.  Then I want back to Places menu and hovered over the icon again and it just said "ftpdrive", it didn't say "mount ftpdrive" anymore.  Also in File Browser, it now has the eject icon.

Can you please post the contents of /etc/fstab .?

---

### Post by audiomick on 2012-04-19
> **Scott216 said:**
> I'm not positive what correctly mounted at start up is, but here's what I tried: 
I rebooted and went to Places menu and I could see an icon for ftpdrive, when I hovered the mouse over it, it said "mount ftpdrive" (which seems to me it's not mounted yet).  I opened File Browser and clicked on ftp drive.  Then I want back to Places menu and hovered over the icon again and it just said "ftpdrive", it didn't say "mount ftpdrive" anymore.  Also in File Browser, it now has the eject icon.

Your assumption is correct: the drive is not mounting automatically at boot. It seems to be able to mount when you do it manually.

I'm not well versed in this, but I think you should look at the bit about system wide mounts in here

[https://help.ubuntu.com/community/AutomaticallyMountPartitions]("https://help.ubuntu.com/community/AutomaticallyMountPartitions")

---

### Post by Scott216 on 2012-04-19
I'm pretty sure my user wasn't created correctly: I don't see the user in Users and Groups application, I can't login as that user, and a home directory was never created on /media/ftpdisk/.  The username is being used somewhere because if I try to add the user again, ubuntu says that name is already in use.

My /etc/fstab file is:

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=6ecebcec-149d-4790-8ec8-1d31becae598 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=66845bcf-e2a9-4ed1-815e-67f796993502 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

---

### Post by Scott216 on 2012-04-19
I tried deleting the user camera1 with, but it said user doesn't exist:

$ sudo userdel -r camera1
userdel: user camera1 does not exist

Then I went to Users and Groups application and tried to add camera1 as a new user and got this error:

User name "camera1" already exists

Seems strange.  I could always come up with a different username, but I would like to know what's going on here.

---

### Post by codemaniac on 2012-04-19
> **Scott216 said:**
> I'm pretty sure my user wasn't created correctly: I don't see the user in Users and Groups application, I can't login as that user, and a home directory was never created on /media/ftpdisk/.  The username is being used somewhere because if I try to add the user again, ubuntu says that name is already in use.

My /etc/fstab file is:

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=6ecebcec-149d-4790-8ec8-1d31becae598 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=66845bcf-e2a9-4ed1-815e-67f796993502 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
The fstab file typically lists all available disks and disk partitions, and indicates how they are to be initialized or otherwise integrated into the overall system's file system.

I cannot see your other hdd automounted , you need an entry in this file for that partition you need to mount at startup .

You need to just append an extra entry for the hdd .
This community doc will help you tweak your /etc/fstab file .
[https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions)
Please back up your /etc/fstab file before doing configuration change .

---

### Post by codemaniac on 2012-04-19
> **Scott216 said:**
> I tried deleting the user camera1 with, but it said user doesn't exist:

$ sudo userdel -r camera1
userdel: user camera1 does not exist

Then I went to Users and Groups application and tried to add camera1 as a new user and got this error:

User name "camera1" already exists

Seems strange.  I could always come up with a different username, but I would like to know what's going on here.

This is somewhat strange . Can you see your user camera1 listed in System Tools-> System Settings -> User Accounts ?

If it is seen try deleting it from by hitting the "-" button .
Attaching a screenshot for your ref .

---

### Post by Cheesemill on 2012-04-19
What format is your 2nd drive?

If it's not a linux filesystem but instead something like NTFS or FAT32 then you cannot use it for a users home directory as it doesn't support the correct permissions.

---

### Post by audiomick on 2012-04-19
> **Cheesemill said:**
> What format is your 2nd drive?

If it's not a linux filesystem but instead something like NTFS or FAT32 then you cannot use it for a users home directory as it doesn't support the correct permissions.

Good point.

---

### Post by Scott216 on 2012-04-19
> **codemaniac said:**
> This is somewhat strange . Can you see your user camera1 listed in System Tools-> System Settings -> User Accounts ?

If it is seen try deleting it from by hitting the "-" button .
Attaching a screenshot for your ref .

I'm using ubuntu 9.04, so I don't see System Tools-> System Settings -> User Accounts, but I do have System > Administration > Users and Groups.  In that I don't see camera1.

I attached a screenshot.

---

### Post by Scott216 on 2012-04-19
> **Cheesemill said:**
> What format is your 2nd drive?

If it's not a linux filesystem but instead something like NTFS or FAT32 then you cannot use it for a users home directory as it doesn't support the correct permissions.

My 2nd drive is FAT32.  I added it to etc/fstab and rebooted and it appears to mount automatically at startup.  

If I reformat so it's a linux filesystem, can I still use it for FTP?  

Maybe I'm going about this all wrong.  All I want to do is give my security camera write access to an FTP drive, but I don't want anonymous FTP login.  I assumed I would just create a new user and make the home directory the ftp drive.  Could I just skip the new user all together and create a username and password using the ftp server?  I'm using vsftpd.

---

### Post by codemaniac on 2012-04-19
Dear Scotty , thanks for the patience and finding out the appropriate  location of settings in your flavor .

Can you try adding camera1 from commandline instead .
```
adduser camera1
```

---

### Post by Scott216 on 2012-04-19
> **codemaniac said:**
> Dear Scotty , thanks for the patience and finding out the appropriate  location of settings in your flavor .

Can you try adding camera1 from commandline instead .
```
adduser camera1
```

I get this:

adduser: The group `camera1' already exists.

---

### Post by Scott216 on 2012-04-19
I figured out the problem with camera1 username.  I went into Users and Groups, then into Groups and deleted the group camera1.  Then I was able to add the camera1 user.  But instead of making the home directory my ftpdrive, I just kept the default /home/camera1/

I still need to figure out how to let my security camera login and save files to my ftpdrive.

---

### Post by audiomick on 2012-04-19
> **Scott216 said:**
> 
If I reformat so it's a linux filesystem, can I still use it for FTP?  [/CODE]
Yes. I'm no expert on this, but I am very sure that this is the case. If the drive is to only be used with a linux install, there is a lot to be said for formatting it to a linux file system.

[CODE]
I assumed I would just create a new user and make the home directory the ftp drive.  Could I just skip the new user all together and create a username and password using the ftp server?  I'm using vsftpd.

I don't know if the way you are approaching this is good or not, but, as has been mentioned, linux user permissions cannot be applied to a non linux file system, and therefore you cannot use a fat32 drive as your /home folder.

I assume you have looked at this?

[https://help.ubuntu.com/10.04/serverguide/C/ftp-server.html](https://help.ubuntu.com/10.04/serverguide/C/ftp-server.html)

---

### Post by Scott216 on 2012-04-19
> **audiomick said:**
> I don't know if the way you are approaching this is good or not, but, as has been mentioned, linux user permissions cannot be applied to a non linux file system, and therefore you cannot use a fat32 drive as your /home folder.

I assume you have looked at this?

[https://help.ubuntu.com/10.04/serverguide/C/ftp-server.html](https://help.ubuntu.com/10.04/serverguide/C/ftp-server.html)

Yes, I've seen that (or something very similar).  I used it to disable anonymous FTP. It doesn't talk too much about setting up users and folder permissions.  From what I gather, when a ftp user logs in, then the ftp directory is the users home directory, which is not what I want.  You can change the home directory, but from this thread I've learned you can't do that if the drive is FAT32.  I guess I could reformat the ftp drive and try creating the home directory there.  But it seems to me I should be able to just give the camera1 user access to the ftp drive, then I could use FTP to write files to that drive.

---

### Post by codemaniac on 2012-04-19
> **Scott216 said:**
> I get this:

adduser: The group `camera1' already exists.

So the group still exists , two options now .
1)Remove the group camera1 and adduser then
2)Adduser to existing camera1 user.

To add new user(camera1) to a existing group (camera1) we would do this:
```
sudo adduser camera1 camera1
```

---

### Post by Scott216 on 2012-04-19
> **codemaniac said:**
> So the group still exists , two options now .
1)Remove the group camera1 and adduser then
2)Adduser to existing camera1 user.

To add new user(camera1) to a existing group (camera1) we would do this:
```
sudo adduser camera1 camera1
```

I deleted the camera1 group. I'm not sure how the camera1 group was created in the first place; I didn't go into groups and create it. It must be a by-product when I created camera1 user. 
Anyway, I was able to add a camera1 user, but I didn't make the home directory the ftp drive, I just kept the default directory Ubuntu recommended.  All that seems to work okay.  Now I need to figure out how enable saving files to the ftpdrive when the security camera is logged in as camera1.

---

### Post by codemaniac on 2012-04-19
exactly when you donot specify a group while creating a new user , sstem will create a grup automatically with the same name of that user .
You can always modify the user in order to allocate him a new home .
usermod command will serve the purpose for you .

---

