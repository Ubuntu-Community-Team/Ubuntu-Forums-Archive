---
title: "Steps I will take to set up, are they correct?"
date: 2014-10-25
forum: New to Ubuntu
---

### Post by Ubu1son on 2014-10-25
I just need help to see if I have chosen the right settings/step to get my system how I want 


I have installed xubuntu 14.04LTS.  I have set up 4 admins, 2 standard users ( a1, a2, a3, a4, u1, u2 ).


There is only one hard drive.  It has 3 partitions - Swap, Root/home (ext4 ), Data (ext4).




**1. ** I checked gparted, and it is showing the Swap partition as having an "active" flag, and RH (root/home) has no flag.  Should these be the other way around?


**2.**  I want to automount the Data partition, and let all 6 users be able to create copy delete new folders without any permission problems.  
     So I will edit fstab:
```
gksudo gedit /etc/ftsab
```

```

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0

# sda2
UUID=0bf11feb /               ext4    errors=remount-ro 0       1

# swap sda1
UUID=c2b3bf0a none         swap    sw              0       0

# sda3 Data
 UUID=gchdir990  /mnt/DATA            ext4          defaults                    0  2 

```

I'm not sure whether defaults will let all users do anything?



**3. **create the mount point for the DATA partition just added to fstab:
```
sudo mkdir /mnt/DATA
```

Then change its permissions:
```
sudo chmod -R a+rwX /mnt/DATA
```


Will this affect the 2 folders on DATA in next step 4 below?



**4. ** The data partition has 2 folders, Private and AllUsers. They were transferred via a live cd from an old ntfs drive. They both (plus sub directories/files) have an "x" on the icon and owner is 999.

I want the Private folder to only be accessible to the 4 admin.  And the AllUsers for everyone.
I have created a new group with the GUI,  called gA and added a1, a2, a3, a4.

I should change permissions for AllUsers folder:
```
sudo chmod -R a=rwX /mnt/DATA/AllUsers
```

And for the Private folder:
```

sudo chgrp gA /mnt/DATA/Private
sudo chmod -R ug=rwX /mnt/DATA
```


Will all of this be overridden by the permissions of the mount point in step 3?



**5. **I want to make the home folders more private.  Can I right click a home folder ( eg /home/a1 ) and change the "others" to none, So when it is clicked by another user it will not open at all?
Will this have any effect on the files/folders in the home folder and if any system processes want access to them?


**6. **The PC will have an old nvidia gt240 card. I want to change the compositor to compton as mentioned on these forums. [http://ubuntuforums.org/showthread.php?t=2144468&p=12644745#post12644745](http://ubuntuforums.org/showthread.php?t=2144468&p=12644745#post12644745)

It says to add PPA's, but I read another place thats its in software center. Can I just install from SC, and will it update normally, or must I add the PPA's?

Next it says:
> you will want to create your compton config file. Save the file as "~/.compton.conf". 

Is this added in the home folder, so /home/a1/.compton.conf?   If so, will these settings only work per logged in user, or for any user that logs in?

There is an example conf settings in the thread to use, but it was posted on late 2013. There is another more newer conf settings posted by user emblem parade [http://ubuntuforums.org/showthread.php?t=2244519&p=13123340#post13123340](http://ubuntuforums.org/showthread.php?t=2244519&p=13123340#post13123340)

Should I use it instead?

I must then Add the command to the auto start-up ```
**compton -b**
```

but again, I find a different post to use 

```
Add:

Name: "Compton"

Description: "Compositor"

Command: "/usr/bin/compton -b"
```


Do they both achieve the same thing?



**7.**
I have old firefox/thunderbird profiles I want to copy over.

I will just log into the account I want to update the profiles for, and then just copy them inside the profiles folders in the home folder.

Will the permissions/ownership be automatically changed to the logged in user, or do I have to change them again?




Hopefully all above will work and system will boot fine, but I really need confirmation if I'm wasting time or have done things correctly...

Thanks!

---

### Post by bab1 on 2014-10-26
> **Ubu1son said:**
> I just need help to see if I have chosen the right settings/step to get my system how I want 


I have installed xubuntu 14.04LTS.  I have set up 4 admins, 2 standard users ( a1, a2, a3, a4, u1, u2 ).

Linux has 3 types of users[LIST]
[*]Root User -- The only administrative user (superuser)
[*]System User - Non-login users the handle system processes only (i.e. mail, news, uucp, lpadmin)) 
[*]Mortal Users -- Login users that humans use (i.e. bill, bob, joe, jdoe, bbaggins)
[*]
[/LIST]
Explain what your 4 admin and 2 standard users are.  My guess is that you have 4 mortal user accounts that have sudo rights and 2 mortal user accounts that do not have sudo rights.  Is this correct? Do all these accounts have home directories at /home?
> 
There is only one hard drive.  It has 3 partitions - Swap, Root/home (ext4 ), Data (ext4).
**1. ** I checked gparted, and it is showing the Swap partition as having an "active" flag, and RH (root/home) has no flag.  Should these be the other way around?

Not sure what you have here.  Post the output of this```
sudo parted -l
```
> 


**2.**  I want to automount the Data partition, and let all 6 users be able to create copy delete new folders without any permission problems.  
     So I will edit fstab:
```
gksudo gedit /etc/ftsab
```

```

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0

# sda2
UUID=0bf11feb /               ext4    errors=remount-ro 0       1

# swap sda1
UUID=c2b3bf0a none         swap    sw              0       0

# sda3 Data
 UUID=gchdir990  /mnt/DATA            ext4          defaults                    0  2 

```

I'm not sure whether defaults will let all users do anything?

All of the references are available in the local system manual.  For details on fstab you can use this command```
man fstab
```...The section on *defaults * says```
 defaults
                     use default options: rw, suid, dev, exec, auto, nouser, and async.

```
For the most part the *defaults * parameter is adequate.  
> 

**3. **create the mount point for the DATA partition just added to fstab:
```
sudo mkdir /mnt/DATA
```

How do you expect your users to access this DATA partition?  Are the multiple users all using this local host at different times or are they accessing this host (computer) remotely?   If the users are remote then we are talking about using this host as a file server; correct?  What method would you be using?  NFS or Samba or...  Are there going to be Windows clients accessing the data? 
> 

Then change its permissions:
```
sudo chmod -R a+rwX /mnt/DATA
```

Will this affect the 2 folders on DATA in next step 4 below?

Not the way you would expect it to.  None of this below is the proper way of setting up shared data for common users.
> 

**4. ** The data partition has 2 folders, Private and AllUsers. They were transferred via a live cd from an old ntfs drive. They both (plus sub directories/files) have an "x" on the icon and owner is 999.

The user 999 indicates you are using a LiveCD booted system.  Permissions and ownership is set at mount time.  The ext4 formatted partitions are checked by the OS at mount time.  NTFS formatted partitions are set via the fstab listing. 

User ownership and permissions of existing data are preserved on a best effort basis.   What this means to you is that it may or may not happen depending on the format of the originating partition.  On the other hand files and directories that are ***created *** have the ownership of *user:user-group* by default.  The system umask sets the default permissions for all files and partitions at 0664 for files and 0775 for directories.  

This is FYI for you as this is is not exactly what you want to accomplish.  You will need to set group inheritance of a common user-group (i.e. staff) if you want multiple users to access common data.  
> 

I want the Private folder to only be accessible to the 4 admin.  And the AllUsers for everyone.
I have created a new group with the GUI,  called gA and added a1, a2, a3, a4.

I should change permissions for AllUsers folder:
```
sudo chmod -R a=rwX /mnt/DATA/AllUsers
```

And for the Private folder:
```

sudo chgrp gA /mnt/DATA/Private
sudo chmod -R ug=rwX /mnt/DATA
```


Will all of this be overridden by the permissions of the mount point in step 3?
[QUOTE]The shared directories should be **below the mount point**.  This will provide you more flexabliity.



**5. **I want to make the home folders more private.  Can I right click a home folder ( eg /home/a1 ) and change the "others" to none, So when it is clicked by another user it will not open at all?
Will this have any effect on the files/folders in the home folder and if any system processes want access to them?
[/QUOTE]
Generally speaking the only processes applied to the data in the users home directory are spawned by that user.  If you use the tool *ls* to list the files in a directory the process runs under your username.  The setting you are referring to is 0770.  Since you are the only user in your *user-group* you could also user 0700.  It has no affect on the files and directories below the directory /home/$USER.  Nor does it need to.



> 
**6. **The PC will have an old nvidia gt240 card. I want to change the compositor to compton as mentioned on these forums. [http://ubuntuforums.org/showthread.php?t=2144468&p=12644745#post12644745](http://ubuntuforums.org/showthread.php?t=2144468&p=12644745#post12644745)


The rest of the questions subjects that should be separate threads in different sections, such as[ Desktop Environments]("http://ubuntuforums.org/forumdisplay.php?f=329") for video and [General]("http://ubuntuforums.org/forumdisplay.php?f=331") for Thunderbird.  I have no real expertise in these subjects.

---

### Post by Ubu1son on 2014-10-26
It seems maybe I made it sound more complex than I needed to.

You're right, I simply made 6 user accounts from within the usergroups GUI, and checked "administrator" for 4 of them, and "standard user" for the other 2.


There is only one HDD in the system. It is partitioned in 3.  
The first partition contains the swap.
The second partition (ext4, boot) is where xubuntu is installed , both /root and /home is there.
The third partition (ext4) I made just for data, thus I will mount it under the mnt/DATA.

I reformatted the swap partition, the 2nd partition now has boot flag.


**3**. The DATA partition, which will be mounted under /mnt/DATA in fstab, will be used by every user.
So anyone who logs on to the pc, should be able to write, read, execute, any file and folder while logged onto their account. All accounts are on the HDD, locally.
So far there is no remote log on or sharing etc..

I changed the permissions of the /mnt/DATA folder using:

```
sudo chmod -R a+rwX /mnt/DATA
```

If I don't do that, no user can create or paste any folders/files on the DATA partition, outside of the 2 folders mentioned below ( private and Allusers).


You mention its not the proper way to share the DATA partition.  Then how would any user be able to rwx on the partition, if I don't change the mount point, and folders' permissions?



**4**. The Private and AllUsers Folders were on a windows system previously. I copied them to a usb HDD, and then copied them to the 3rd partition ( DATA, ext4) while using a live CD.
I want to change the owners and permissions so that all the 4 admins have complete access, write, read, and execute. 
I don't want the 2 standard users to be able to open the Private folder.  Thats why I made the group gA.
I ended up changing the group to gA( read and write) and "none" for "others" from the GUI, not sure if this is different from doing it in terminal.

Concerning the Home folders of each user.  I just right clicked the folder, chose "none" for "others".  It asked if I wanted to apply to all files/folders in the home folder, and I chose Yes.
It popped with a few "permission denied" windows, I skipped for all.  It worked as intended, now the home folders ( pics,  vid, docs etc ) are not readable by other users. 
I'm not sure if choosing "none"  will affect all the other files and folders in the home folder though?


I will make new thread for the other Q's.


Thanks again.

---

### Post by bab1 on 2014-10-26
> **Ubu1son said:**
> It seems maybe I made it sound more complex than I needed to.

You're right, I simply made 6 user accounts from within the usergroups GUI, and checked "administrator" for 4 of them, and "standard user" for the other 2.


There is only one HDD in the system. It is partitioned in 3.  
The first partition contains the swap.
The second partition (ext4, boot) is where xubuntu is installed , both /root and /home is there.
The third partition (ext4) I made just for data, thus I will mount it under the mnt/DATA.

I reformatted the swap partition, the 2nd partition now has boot flag.


**3**. The DATA partition, which will be mounted under /mnt/DATA in fstab, will be used by every user.
So anyone who logs on to the pc, should be able to write, read, execute, any file and folder while logged onto their account. All accounts are on the HDD, locally.


So far there is no remote log on or sharing etc..

I changed the permissions of the /mnt/DATA folder using:

```
sudo chmod -R a+rwX /mnt/DATA
```

If I don't do that, no user can create or paste any folders/files on the DATA partition, outside of the 2 folders mentioned below ( private and Allusers).


You mention its not the proper way to share the DATA partition.  Then how would any user be able to rwx on the partition, if I don't change the mount point, and folders' permissions?

When you mount partitions you are really mounting the file system on the partition to a place in the existing root file system (/ = root file system).  Although you can mount the partitions file system anywhere below /; the convention is to mount common data file systems at either /usr/local/share for local users or /srv for remote users.  /mnt is for temporary mounts of data.  See [here]("http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard") for more on the Linux file system hierarchy.  That being said, I would mount the data at /data.  That way there is no mistaking where the data resides.
> 

**4**. The Private and AllUsers Folders were on a windows system previously. I copied them to a usb HDD, and then copied them to the 3rd partition ( DATA, ext4) while using a live CD.
I want to change the owners and permissions so that all the 4 admins have complete access, write, read, and execute. 

All the admins have access to everything on the system.  They are all part of the sudoers group which allows them to switch to root and use of the root powers.  Read the information on sudo [here]("https://help.ubuntu.com/community/RootSudo").  You can read about the */etc/sudoers* configuration file [here]("https://help.ubuntu.com/community/Sudoers").
> 

I don't want the 2 standard users to be able to open the Private folder.  Thats why I made the group gA.
I ended up changing the group to gA( read and write) and "none" for "others" from the GUI, not sure if this is different from doing it in terminal.

You are on the right track here.  There are built in groups for this already (adm, staff, users).  The file system can be something like this```

/data
       /private
       /public

```
Then you just use different group ownership for each sub-directory.  The owner of the subdirectory can be root.  Using this the ownership of the sub-directories would look like this```

/data/private = root:staff

/data/public = root:users

```
I assume the all users would be in the *users group* and the admins would also be in the *staff group*.  You need to set group inheritance so that any future data has the correct group ownership.  This will insure that the proper users always have access to the data.  Without setting the group ownership you are doomed to always having rwx for everything.  Meaning you can't limit access at all. 
> 

Concerning the Home folders of each user.  I just right clicked the folder, chose "none" for "others".  It asked if I wanted to apply to all files/folders in the home folder, and I chose Yes.
It popped with a few "permission denied" windows, I skipped for all.  It worked as intended, now the home folders ( pics,  vid, docs etc ) are not readable by other users. 
I'm not sure if choosing "none"  will affect all the other files and folders in the home folder though?


I will make new thread for the other Q's.


Thanks again.
If you are going to learn Linux you should learn how to use commands at the CLI (terminal prompt).  The control is more precise and you get to see how things really look under the Pretty GUI interface.

Do you want to try some CLI commands?

---

### Post by mastablasta on 2014-10-27
> **Ubu1son said:**
> 

I have installed xubuntu 14.04LTS.  I have set up 4 admins, 2 standard users ( a1, a2, a3, a4, u1, u2 ).

There is only one hard drive.  It has 3 partitions - Swap, Root/home (ext4 ), Data (ext4).

**2.**  I want to automount the Data partition, and let all 6 users be able to create copy delete new folders without any permission problems.  


Why didn't you select the mount point for data during install then?     


> 
**5. **I want to make the home folders more private.  Can I right click a home folder ( eg /home/a1 ) and change the "others" to none, So when it is clicked by another user it will not open at all?
Will this have any effect on the files/folders in the home folder and if any system processes want access to them?


this doesn't make sense. administrators (sudo group) will be able to see everyone's folder. though not by default.

otherwise /home/user is from user. you can think of it kind of as "my documents"/documents folder. it holds user settings and configurations. it doesn't influence other user. programs are stored in a different directory.

also I am guessing this is a server? if so then why are you using a desktop on it?
You can use GUI that was designed for servers. Have a look at Zentyal (ubuntu based) or for example Ajenti. perhaps it will be easier for you to administer the server via such a specific server GUI. you can connect to server via web browser and administer it like that. or Zentyal also has a desktop available for the interface.

---

### Post by Ubu1son on 2014-10-27
> **bab1 said:**
> /mnt is for temporary mounts of data.  See [here]("http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard") for more on the Linux file system hierarchy.  That being said, I would mount the data at /data.  That way there is no mistaking where the data resides.

So even if I mount it at /DATA, would I not still need to change the permissions/ownership to do what I want?

> All the admins have access to everything on the system.  They are all part of the sudoers group which allows them to switch to root and use of the root powers.  Read the information on sudo [here]("https://help.ubuntu.com/community/RootSudo").  You can read about the */etc/sudoers* configuration file [here]("https://help.ubuntu.com/community/Sudoers").

Yep, but they will not be using terminal or sudo hardly ever, but they need to be able to install software, and do updates, drivers etc..  So even though they *can* do anything, they still need to be able to copy/write/read/delete etc anything on DATA without resorting to sudo.

> You are on the right track here.  There are built in groups for this already (adm, staff, users).  The file system can be something like this
```

/data
       /private
       /public

```
Then you just use different group ownership for each sub-directory.  The owner of the subdirectory can be root.  Using this the ownership of the sub-directories would look like this```

/data/private = root:staff

/data/public = root:users

```
I assume the all users would be in the *users group* and the admins would also be in the *staff group*.  You need to set group inheritance so that any future data has the correct group ownership.  This will insure that the proper users always have access to the data.  Without setting the group ownership you are doomed to always having rwx for everything.  Meaning you can't limit access at all. 

Does it matter who the owner is, whether root or an admin?
Would I not need to set up the same for the DATA mountpoint, so that any future data can also be set up anywhere on the DATA partition, that is, other than the 2 folders?

> If you are going to learn Linux you should learn how to use commands at the CLI (terminal prompt).  The control is more precise and you get to see how things really look under the Pretty GUI interface.

Do you want to try some CLI commands?

Yes, I tried already the CLI for the home folders, but thought maybe the GUI setting of the "other" setting would be less risk of harm.
I didn't try command straight up, because most commands I come across in guides, are old, then  a newer guide states a better command, and so on...


> **mastablasta said:**
> Why didn't you select the mount point for data during install then?     

I set up the data partition after install.


> this doesn't make sense. administrators (sudo group) will be able to see everyone's folder. ***though not by default***.

That's the main reason for the data partition settings, they will be only using it as default.   As for the home folders, well even a standard user can see anyone elses docs, pic, vid etc by default, which is why it must be changed to private in my opinion.


> also I am guessing this is a server? if so then why are you using a desktop on it?

Its not a server, its a desktop pc, for normal windows users.

---

### Post by mastablasta on 2014-10-27
> **Ubu1son said:**
> 
That's the main reason for the data partition settings, they will be only using it as default.   As for the home folders, well even a standard user can see anyone elses docs, pic, vid etc by default, which is why it must be changed to private in my opinion.

Its not a server, its a desktop pc, for normal windows users.

making it 700 should close it for others. you can right click and select permissions, then you should be able to give permission for example only for the user. e.g. group users can not read, write or execute in that folder only user can. and then set it to go down the directory structure. there are some folder where this is advised to be done anyway. like for example /.ssh (if you are using ssh to connect to the computer from outside of LAN network).

however as soon as admin opens file manager as root (e.g. gksu nautilus) they will be able to see everything.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

so regarding permissions : [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

you basically have owner, then you have group and finally there is public (or everyone). for each file and each directory you need to see if the person/group can read, write or execute a file. 
in your case what you want to do is give full power to the user (at least in home), yet no powers (read, write and execute) in the directory for the group and for public/everyone. should be easy enough to do in file manager GUI. if it gives you problems run it as root (gksu nautilus in ubuntu) but it should be possible for each user to have it locked down as they want to.

edit - just one more thing  If you check the ubutnu manual in my signature it is a bit better explained. maybe easier how to administer users and files and direcotries. there is a folder called Public in home folder that I use to share with other users. in that one others can read and write but not in other fodlers in /home.

you could also attach common folders via symbolic links into each user's home folder. that way it would feel to them like their folders are on /home but in reality they are on different partition.

---

### Post by bab1 on 2014-10-27
> **Ubu1son said:**
> So even if I mount it at /DATA, would I not still need to change the permissions/ownership to do what I want?

Wherever you mount the partition you will have to configure the ownership/permissions and inheritance.  I'm suggesting that you also learn the conventions of administering a Linux system. As an example, I would use /data not /DATA as a mountpoint.  /DATA is a Windows paradigm.  you will learn to hate caps if you use the CLI for any length of time. 
> 
Yep, but they will not be using terminal or sudo hardly ever, but they need to be able to install software, and do updates, drivers etc..  So even though they *can* do anything, they still need to be able to copy/write/read/delete etc anything on DATA without resorting to sudo.

Sudo can be configured for single operations and GUI commands too.  Any sudoer can install programs and do updates along with adding drivers (modules).  When you invoke a command such as *synaptic* to install an app it first asks for your login if you are a sudoer.  This is sudo at work.
> 
Does it matter who the owner is, whether root or an admin?

The user ownership does not matter in this case.  The group ownership is the key.  All users in the group are allowed access based on those permissions.  But access is only part of the equation.  You need to preserve that group ownership when a file or directory is created too.  This is done by using the set group ID bit (sgid) at the root of the mounted file system (the mounted partition). 
> 
Would I not need to set up the same for the DATA mountpoint, so that any future data can also be set up anywhere on the DATA partition, that is, other than the 2 folders?

That's the inheritance I have been talking about.  If you use the *sgid* bit at the root of the file system (in your case /data/public and /data/private then the group ownership is inherited form that group.  For example if I change the group owner to staff on the directory /data/private (chgrp staff /data/private) and set the group ID bit (sudo chmod 2775 /data/private) then all subsequent files and directories will  have *staff* as the group owner.  Thus all users in the group *staff* will have access. 
> 

Yes, I tried already the CLI for the home folders, but thought maybe the GUI setting of the "other" setting would be less risk of harm.
I didn't try command straight up, because most commands I come across in guides, are old, then  a newer guide states a better command, and so on...

The command line tools are the same going back to the very beginning.  New tools may be added, but the old tools will work fine.  The GUI uses the same tools for the most part.  Just wrapped in a visual package with arbitrary limitations.
> 

That's the main reason for the data partition settings, they will be only using it as default.   As for the home folders, well even a standard user can see anyone elses docs, pic, vid etc by default, which is why it must be changed to private in my opinion.

It's not really up to the system admin to block access to a users home directory.  The user has that option.  You can show them or even offer to block access for them, but the user has control to set it however they want.  The user can't block the root user however so the admin always has access.
> 
Its not a server, its a desktop pc, for normal windows users.
The computer can be both a workstation (desktop) and have servers.  The term Server, as in Ubuntu Server or Windows Server is a marketing term.  The term server as in web server or DNS server refers to a process running on a host (computer) waiting for a client request for services.  You can have services running on any host.

I'm curious what do you mean by this: "a desktop pc, for normal windows users"?

---

### Post by Ubu1son on 2014-10-27
> **bab1 said:**
> 
Sudo can be configured for single operations and GUI commands too.  Any sudoer can install programs and do updates along with adding drivers (modules).  When you invoke a command such as *synaptic* to install an app it first asks for your login if you are a sudoer.  This is sudo at work.

I realize sudo is behind the GUI when it asks for password for example.  What I meant was, they will not be deliberately using sudo, through terminal or otherwise, other than the default prompts.


> That's the inheritance I have been talking about.  If you use the *sgid* bit at the root of the file system (in your case /data/public and /data/private then the group ownership is inherited form that group.  For example if I change the group owner to staff on the directory /data/private (chgrp staff /data/private) and set the group ID bit (sudo chmod 2775 /data/private) then all subsequent files and directories will  have *staff* as the group owner.  Thus all users in the group *staff* will have access. 

OK, so lets say they want to create another folder on the partition ( /data/newfolder ), then I must also set the groupID for the mountpoint for all 6 users?  Will this not have an effect on the group settings of the private folder, which allows only the admin group?


> The command line tools are the same going back to the very beginning.  New tools may be added, but the old tools will work fine.  The GUI uses the same tools for the most part.  Just wrapped in a visual package with arbitrary limitations.

I was more referring to different commands for the same outcome, eg. a post mentions a+rwx  then a newer post a+wrX, the first post not making a distinction between the 2 commands and the importance of x/X

> It's not really up to the system admin to block access to a users home directory.  The user has that option.  You can show them or even offer to block access for them, but the user has control to set it however they want.  The user can't block the root user however so the admin always has access.

I didn't mean that admin block access to a users home, rather a user expecting their home/pictures being private and not readable by all other users on the pc for instance.


> The computer can be both a workstation (desktop) and have servers.  The term Server, as in Ubuntu Server or Windows Server is a marketing term.  The term server as in web server or DNS server refers to a process running on a host (computer) waiting for a client request for services.  You can have services running on any host.

yeah, I just took the post to mean a server without any local users, as they did ask whether it was a server or desktop. Well that's how I understood the question form a windows point of view ;)

> I'm curious what do you mean by this: "a desktop pc, for normal windows users"?

what I mean is, they are normal desktop users with experience only in normal windows desktops.
So they must be able to update, install software without terminal, change settings etc. A GUI password prompt is fine.  As far as I'm aware, you must be admin with sudo to do this. So they will be admins.
The standard users don't need to install or change anything.

---

### Post by bab1 on 2014-10-27
> **Ubu1son said:**
> OK, so lets say they want to create another folder on the partition ( /data/newfolder ), then I must also set the groupID for the mountpoint for all 6 users?  Will this not have an effect on the group settings of the private folder, which allows only the admin group?

Once the mountpoint of /data is created and the partition mounted at that position, there is no more need to deal with the mountpoint itself.  We would mount the partition via instructions in the /etc/fstab file.

All directories are now created BELOW this point of /data (e.g. /data/newdirectory.  Each new-directory could be considered a starting point for a new file system with a different group controlling it.  Kind of like a fork in the road starts a new road. 
> 
I was more referring to different commands for the same outcome, eg. a post mentions a+rwx  then a newer post a+wrX, the first post not making a distinction between the 2 commands and the importance of x/X

The example you used is the same command with different "switches" (e.g. x vs X).   The man pages or Google will show the differences.  That specific example has to do with setting the executable bit on everything (x) vs setting the executable bit only on existing executable scripts (X).
> 
I didn't mean that admin block access to a users home, rather a user expecting their home/pictures being private and not readable by all other users on the pc for instance.

This is more a philosophical thought.  You are thinking for the user rather than letting the user think for themselves.  Not a big deal in this case. 
> 
yeah, I just took the post to mean a server without any local users, as they did ask whether it was a server or desktop. Well that's how I understood the question form a windows point of view ;)

You are better served (pun intended) thinking of Linux in Linux terms rather than in Windows terms.
> 
what I mean is, they are normal desktop users with experience only in normal windows desktops.
So they must be able to update, install software without terminal, change settings etc. A GUI password prompt is fine.  As far as I'm aware, you must be admin with sudo to do this. So they will be admins.
The standard users don't need to install or change anything.
Ahhhh.   If you are a sudoer you can administrate.  Admin in this case is a verb.  ;-)

---

### Post by mastablasta on 2014-10-28
sudo users can change their own settings in home folder as they please. they can also change settings in their folder in data partition.

---

### Post by Ubu1son on 2014-10-31
> **bab1 said:**
> Once the mountpoint of /data is created and the partition mounted at that position, there is no more need to deal with the mountpoint itself.  We would mount the partition via instructions in the /etc/fstab file.

All directories are now created BELOW this point of /data (e.g. /data/newdirectory.  Each new-directory could be considered a starting point for a new file system with a different group controlling it.  Kind of like a fork in the road starts a new road.

OK, so the mountpoint will only use whats in fstab, which I have as defaults ( as in first post ).
Now, only the two folders, Private and Allusers, will be modified with the group id, chmod etc to work as needed.

But, IF, a standard user or admin creates a new folder on the partition, what rules will it follow?  because if I run no commands on the mountpoint, then no user can create new folders on the partition. 
I want it so any user can create a new folder or files on the partition by default, without affecting the settings of the private and all users folders.


> You are better served (pun intended) thinking of Linux in Linux terms rather than in Windows terms

I'm not sure really, it's just that mastablasta asked earlier: 
> also I am guessing this is a server? if so then why are you using a desktop on it? 			 		 	 

And I replied: 
> Its not a server, its a desktop pc, for normal windows users. 		

The question sounded like there is a distinction between the two, I replied based on the question. If a server and desktop means something totally different on linux than other OS's, then I guess I didn't understand the question ;)





> Ahhhh.   If you are a sudoer you can administrate.  Admin in this case is a verb.  ;-)

So for any user to update or install software or connect a printer, then their account should be created as administrator, which automatically includes them in the sudo group. I'm assuming that's the correct way.




Also, I checked the "users" group in group settings, and no user is checked by default. Should they be, and if a new user account is created, it means they will not by default be part of the "users" group?

---

### Post by bab1 on 2014-10-31
> **Ubu1son said:**
> OK, so the mountpoint will only use whats in fstab, which I have as defaults ( as in first post ).
Now, only the two folders, Private and Allusers, will be modified with the group id, chmod etc to work as needed.

There is a difference between the "mount point" and the directory that is mounted there. I would chmod the mounted directory if you wanted the same parameters on the entire partition, or you can chmod the individual sub folders if you like (or need different parameters).  The ownership (group-owner) of any file/directory object is only affected by the SGID bit set on the parent folder
> 

But, IF, a standard user or admin creates a new folder on the partition, what rules will it follow?  because if I run no commands on the mountpoint, then no user can create new folders on the partition.
 
I want it so any user can create a new folder or files on the partition by default, without affecting the settings of the private and all users folders.

You get to set the ownership and permissions initially and it is automagic after that.
> 

So for any user to update or install software or connect a printer, then their account should be created as administrator, which automatically includes them in the sudo group. I'm assuming that's the correct way.

Yes> 

Also, I checked the "users" group in group settings, and no user is checked by default. Should they be, and if a new user account is created, it means they will not by default be part of the "users" group?
That is correct.  You need to add the "users" group to any users secondary groups if you want them to participate.  These are set by the systems admin and can vary on any system.  It is an option not the default.

At this point you should try some of these commands out.  You won't truly understand until you try it out.

---

### Post by Ubu1son on 2015-03-08
I've had xubuntu14.04LTS running fine with all the info from this thread.


I've now added an ssd drive and have a full hdd that uses ntfs.



So I just wanted to know, can I use the same solutions for this change and add the following (BOLD) to my current setup?



```
# sda2  ADD noatime for changing hdd to SSD
UUID=0bf11feb /               ext4    **noatime,**errors=remount-ro 0       1

# swap sda1
UUID=c2b3bf0a none         swap    sw              0       0

# sda3 Data
 UUID=gchdir990  /data            ext4          defaults                    0  2

[B]# sda4 DATA NTFS
UUID=DA9056 /datantfs ntfs defaults,nls=utf8,umask=000,uid=1000,windows_names 0 0[/B]




```



Remember I have admins/users: a1,a2,a3,a4 (g=admins),u1,u2 (g=admins+users)

on the ext4 data partition mounted at /data (chown a1:a1 )
then folders created on /data:
                                       /Private       ( chown a1:admins  -  chmod 2770 )
                                       /allusers      (  chown a1:users   -   chmod 2775 )


It all seems to work as intended, except if a any user/admin creates a new folder on /data ( that is, outside of the private and allusers folders), then that folder group is set as the user and not the group the user is in.




So, is the fstab correct?
And can similar be set up for the datantfs partition, as in:
/datantfs
            /private
            /allusers

and the same admins/users/groups/permissions set as above for the ext4 /data partition?

Or it will not work for an ntfs partition, and all users/admins will have complete read/write/execute control of all and any folders/files?

oh, and will I have to use
```
sudo chmod -R a+rwX
```
on all the folders/files that are presently on the ntfs partition?

---

### Post by mastablasta on 2015-03-09
Linux permissions do not work on NTFS. they work on  Linux file systems (ext3, ext4, ZFS4linux, BTRFS ...) which are far more advanced than NTFS.

on previous question - Ubuntu Server version is made for headless server (computer with no monitor present) so it comes without a desktop but with a bunch of other server applications (e.g. for email server, proxy, security for open ports etc). desktop can be added later though.
Ubuntu Desktop comes with desktop and various desktop applications such as office programs, web browser etc. it is ment to be run on a PC with a monitor attached. has a graphics interface for various things, including file manager where one can set folder permissions and such via GUI.

---

### Post by Ubu1son on 2015-03-10
> **mastablasta said:**
> Linux permissions do not work on NTFS. they work on  Linux file systems (ext3, ext4, ZFS4linux, BTRFS ...) which are far more advanced than NTFS.


SO setting any sort of permissions/chown/chmod on any folders/files on the ntfs partition will not work, and all users/admins will have  complete read/write/execute control of all and any folders/files?


Is the entry I added in bold ( previous post) to the fstab correct for ntfs partitions?


> on previous question - Ubuntu Server version is made for headless server (computer with no monitor present) so it comes without a desktop but with a bunch of other server applications (e.g. for email server, proxy, security for open ports etc). desktop can be added later though.
Ubuntu Desktop comes with desktop and various desktop applications such as office programs, web browser etc. it is ment to be run on a PC with a monitor attached. has a graphics interface for various things, including file manager where one can set folder permissions and such via GUI.

Sorry, you lost me here, what is that in reply too? :p

---

### Post by sotiris2 on 2015-03-10
I believe that the permissions of the mount point (the folder /ntfsdata on your root partition) will apply to every ntfs parition totally (as in all folders and files of that filesystem will match the mount point's permissions and have the same owner).

Keep in mind that anybody with full access to sudo can simply become root and check your files regardless of permissions and ownership.

---

### Post by Ubu1son on 2015-03-10
OK, say I have 2 ntfs partitions on the hdd, then I can mount them under the same mount point like this:

```
# sda2  ADD noatime for changing hdd to SSD
UUID=0bf11feb /               ext4    **noatime,**errors=remount-ro 0       1

# swap sda1
UUID=c2b3bf0a none         swap    sw              0       0

# sda3 Data
 UUID=gchdir990  /data            ext4          defaults                    0  2

[B]# sda4 DATA NTFS partition 1
UUID=DA9056 /datantfs/p1 ntfs defaults,nls=utf8,umask=000,uid=1000,windows_names 0 0
[/B]
[B]# sda5 DATA NTFS partition 2
UUID=DA9056 /datantfs/p2 ntfs defaults,nls=utf8,umask=000,uid=1000,windows_names 0 0[/B]





```




so the mountpoints will be

/datantfs/p1
            /datantfs/p2


Now does it matter what is set as the owner and permission for the folders datantfs, p1 and p2, since its ntfs file system, or will it have an effect on which users can RWX files/folders on the mounted partitions?
Doesnt the fstab also have an effect on which user has what permissions?

---

### Post by Ubu1son on 2015-03-14
Well I set up the mount points as above in fstab :


```
[B]# sda4 DATA NTFS partition 1
UUID=DA9056 /datantfs/p1 ntfs defaults,nls=utf8,umask=000,uid=1000,windows_names 0 0
[/B]
[B]# sda5 DATA NTFS partition 2
UUID=DA9056 /datantfs/p2 ntfs defaults,nls=utf8,umask=000,uid=1000,windows_names 0 0
[/B]
```

and the folders:

/datantfs/p1
/datantfs/p2


It seems, any user ( admins or users ) can create, read, edit, delete any file or folder currently on the ntfs  partitions or newly created by any user. 
Even if I use chown or chmod on the mount points, the owner and permissions stay the same and are grayed out ( I assume that's to do with the uid in fstab, but even if that is deleted, the owner becomes
root, and cant be changed. All users can still read/write regardless ).



Another thing I noticed is no user can move anything to the trash, they can only delete. 
I thought it also might have to do with uid, so I changed it to:
```
**defaults,nls=utf8,umask=000,gid=1000,windows_names 0 0**
``` 

removed the uid, and included gid of the group with all user accounts added. Still cant move to trash, only delete.

---

### Post by Ubu1son on 2015-03-17
It seems no matter who owner is, can't move files to trash.  Is it just because its an ntfs partition thats mounted?

---

### Post by mastablasta on 2015-03-17
if you want to use Linux permission system then use Linux file format. I am not sure why you are using NTFS on Linux. NTFS is usually used when users dual (multi) boot and need a data partition accessible by both (all) systems. or when people are lazy like me and just put their stuff on NTFS external disk since it already came that way preformatted. otherwise it is problematic not just because of permissions, but beca use there are no or very limited tools to maintain that file system under Linux. e.g. you need "checkdisk", you need defragmentation etc.


further of note is that physical access is data access. anyone can boot a live OS and access the data from other users. so in your case users make sense just to separate their data. you won't protect the data like that unless you encrypt it. but that can bring more problems than benefits unless you know how to set it up properly and that you have a tested automated backup available.

as for the trash - ntfs is not the reason for it not working. I have it on FAT32 (even when I do not want it). but the file is usually hidden and on disk, not in trash. someone else will have to enlighten you how this system works. but as I understand it unless you set it there wise additional disks move deleted file into their disk's own hidden folder

e.g. I have "data" disk and that data disk has a hidden folder when files are moved before being permanently deleted. I am not sure but I believe those files do not appear in trash. but i could be wrong I need to check this at home where Linux computer's are.

---

### Post by Ubu1son on 2015-03-20
I have an ntfs drive that is nearly full, I cant transfer to any other hdd that has ext4. 
I have to use this for now.

So, I take it, permissions will not work for individual folders/files, and moving to trash wont work, only delete, or can this be somehow acheived with the fstab configuration?


Right now, even though root is owner of the mountpoint ( from fstab ), any local user account can read,write,execute on the ntfs partition. But it seems moving to trash isnt creating the folder needed for each user....

---

### Post by Ubu1son on 2015-04-09
Actually 2 things I noticed with the mounted ntfs partition.

1. A user cant move files to trash, only delete.

2. A fie cant be moved to another folder on the same partition. So cut/paste or dragging to different directory on same partition/mount point begins to copy the files rather than move.


Are these problems to do with the fstab entry?

```
# sda4 DATA NTFS partition 1
UUID=DA9056 /datantfs/p1 ntfs defaults,nls=utf8,umask=000,uid=1000,windows_names 0 0

and 

# sda4 DATA NTFS partition 1
UUID=DA9056 /datantfs/p1 ntfs defaults,nls=utf8,umask=000,gid=1000,windows_names 0 0
```

---

### Post by mastablasta on 2015-04-09
could be. I know I can put in trash on FAT32 so probably it also works on NTFS - then again I have only one user. I also know that one can move on NTFS since I do it all the time on RPi that serves as media center.

---

### Post by Ubu1son on 2015-04-09
Are your ftsab entries any different for ntfs mounts?

I could understand trash not working( for all users btw ) being from fstab/permissions, but how can ftsab or permissions replace moving with copying only...

---

