---
title: "Cannot access drive/share/folder in Samba and Linux at the same time"
date: 2014-04-18
forum: New to Ubuntu
---

### Post by Kristoffer_Selbekk on 2014-04-18
Hello!

So after juggling around with probably 5-6 reinstalls, including Windows and Linux, I finally stopped at Ubuntu Desktop 12.04 LTS. 
This is going to be the OS for my workshop/fileserver

Now, here's the deal. I've successfully set up a samba share through an utility, and can access it no problem on my Windows desktops. BUT, I can't for the life of my access the same share/folder/drive on the server itself. Whenever I try to access that folder it says I do not have permission, and when I then run sudo chown myusername and my share to give the account there the permission, I can access it on the Ubuntu server. 
However, when I do that, I can't access the share on Samba. So, it's either way for me. And then, if i run sudo chown nouser.nogroup and then the directory I get access on the samba share, but not on the server itself. 

I need this since I will be transferring files both on the server and over the network + I have torrent software which will store the downloads on that drive. 

So, what am I doing wrong? 

Cheers, 
Kristoffer

---

### Post by bab1 on 2014-04-18
All the users of the SMB/CIFS share (Samba) should have file and directory access.  Are you logged in with the same user name on both the Windows machine and Ubuntu machine?  

What does the share definition look like?

---

### Post by Kristoffer_Selbekk on 2014-04-18
Hey!

Yep, I am using the same user, however as I see it Samba creates a new user for the samba share anyway. If so, the only difference I know of is on ubuntu it's "kristoffer" whereas on windows it's "Kristoffer"

Do you want a copy of the /etc/samba/smb.conf file?

---

### Post by bab1 on 2014-04-18
> **Kristoffer_Selbekk said:**
> Hey!

Yep, I am using the same user, however as I see it Samba creates a new user for the samba share anyway. If so, the only difference I know of is on ubuntu it's "kristoffer" whereas on windows it's "Kristoffer"


Samba does not create a new user automatically.  Samba does have it's own user database.  You can see it with this command```
sudo pdbedit -L
```
For samba to work properly with the Ubuntu file system permissions you should have both an Ubuntu user and samba user on the Ubuntu machine.  To create the samba user you use this command (using the appropriate username)```
sudo smbpasswd -a <username>
```
> 

Do you want a copy of the /etc/samba/smb.conf file?
Nope.   I'm only interested in the share definitions that you have in the smb.conf file.  If you post it, please put it inside ```
 blocks by using the [SIZE=4]**#**[/SIZE] icon at the top right of the of the advanced response editor.

Also post the output of this (the directory you have shared)[CODE]ls -l <directory>
```

---

### Post by Kristoffer_Selbekk on 2014-04-18
Thanks for the quick reply.

Here is the output "sudo pdbedit -L" gives

```
kristoffer@FIL-SERVER:~$ sudo pdbedit -L
nobody:65534:nobody
kristoffer:1000:Kristoffer S


```

Here is the share definitions, on the bottom of the smb.conf file

```

[Media]
        path = /media/MEDIA
        writeable = yes
;       browseable = yes
        guest ok = yes


```

And, at last, here is the output of the "ls -l" command.


```

kristoffer@FIL-SERVER:~$ ls -l /media/MEDIA/
total 20
drwxr-xr-x 2 kristoffer kristoffer  4096 Apr 18 11:58 Downloads
drwx------ 2 kristoffer kristoffer 16384 Apr 18 11:25 lost+found


```

EDIT: Please note this is when I have used 
```

sudo chown kristoffer <directory>
OR
sudo chown kristoffer.nogroup <directory>

```


I hope this helps. 

Thank you for the help, 
cheers,
Kristoffer

---

### Post by bab1 on 2014-04-18
> **Kristoffer_Selbekk said:**
> Thanks for the quick reply.

Here is the output "sudo pdbedit -L" gives

```
kristoffer@FIL-SERVER:~$ sudo pdbedit -L
nobody:65534:nobody
kristoffer:1000:Kristoffer S


```
This is correct.  The user nobody is the anonymous user (a guest)  > 

Here is the share definitions, on the bottom of the smb.conf file

```

[Media]
        path = /media/MEDIA
        writeable = yes
;       browseable = yes
        guest ok = yes


```

Why did you make the share non-browseable and allow guest access.  When you do this all the files and directories created are owned by the user *nobody* and the group *nogroup*.  Is this what you intended? No login?
> 

And, at last, here is the output of the "ls -l" command.


```

kristoffer@FIL-SERVER:~$ ls -l /media/MEDIA/
total 20
drwxr-xr-x 2 kristoffer kristoffer  4096 Apr 18 11:58 Downloads
drwx------ 2 kristoffer kristoffer 16384 Apr 18 11:25 lost+found


```

EDIT: Please note this is when I have used 
```

sudo chown kristoffer <directory>
OR
sudo chown kristoffer.nogroup <directory>

```

The point was to see what it was like *before *alter it.  :-)
> 

I hope this helps. 

Thank you for the help, 
cheers,
Kristoffer
It sounds like nobody:nogroup is not what you wanted.  So, why are you using *guest ok = yes *? Are you going to be the only user?  Samba is flexible  enough to accommodate just about any scheme.  Here is the share definition for my public share```

[Public]
        comment = Shared Data
        path = /srv/public
        browseable = yes

        force group = users
        writeable = yes

        create mask = 0664
        force directory mode = 2775


``` 
Although my Public share is open to all of my network users, it is not open to any guests.  The group is common to all of the users on my network and the permissions are enforced via the create mask and directory mode.  I could have just as easily have added *guest ok = yes *.  The ownership at that point would be nobody:users and I still would have access.

I would start with adding yourself to the user group ***users***.  Then modify the share definition to what I have and restart the smbd daemon with this command```
sudo service smbd restart
```

At that point you should be able to browse for the share and login, or, if you have enabled guest the share will be available.  You should be able to browse for the share on either the Windows machine or the Ubuntu machine.

On last thing.  You should configure group ownership inheritance.  It is accounted for any new directories created but not for the root directory of the share.  That is set with the SGID bit being set (the 2 in the 2775 for directory permissions),  If the share works we can deal with directory inheritance next.

---

### Post by Kristoffer_Selbekk on 2014-04-19
Okay, so I did all the steps above and it worked! :D

I really don't know what I was thinking when I configured it, but as you say, this is intended for one user only, no guest access (not to this date at least) 
Or, with time I might add some more users, but not anything except that.

So basically, *if* I want to give guest access to the directory, should I only then adjust the settings in the smb.conf file accordingly? 
Or will that also give them access to write to the drive? 

The share always has been showing up when searching for network drives, the problem was just that whenever I opened it with the wrong settings I got "This drive is not accessible" in Windows.

But, as you said, does this mean that the permission that my Ubuntu user has of the drive, will also be shared by the Samba user?

And, this bit at the bottom here
```
[COLOR=#000000][FONT=Ubuntu Mono] 
      create mask = 0664
[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]force directory mode = 2775
[/FONT][/COLOR]
```

How is the permissions built up? I know the 0 in front of the 0664 shouldn't matter, but what do the numbers mean and how are they separated? 

Anyway, thanks for the help, I really appreciate it! I actually was on the end of formatting the drive and install 2008 R2 on the machine (yet again), but I figured I should try to fix the problems I had instead :P

Cheers,
Kristoffer

---

### Post by bab1 on 2014-04-19
> **Kristoffer_Selbekk said:**
> Okay, so I did all the steps above and it worked! :D


Great!
> 

So basically, *if* I want to give guest access to the directory, should I only then adjust the settings in the smb.conf file accordingly? 
Or will that also give them access to write to the drive?

As it is set up now the guest would be allowed to read and write files if you gave access.  After all we created a public share.  The degree that we have restricted users is who is allowed rather than what the user can do.  Samba provides access via authentication (who are you).  Ubuntu provides authorization via permissions (you are allowed).
> 
... does this mean that the permission that my Ubuntu user has of the drive, will also be shared by the Samba user?

Consider this:  An Ubuntu user does not necessarily need to be a Samba user, but the Samba user always needs to be an Ubuntu user.  All users that are authenticated to your share have access and permissions to everything below the share root.  This means that if you had something like this```
/srv/private/samba/[COLOR="#FF0000"]public[/COLOR] 
```... and then created a share at that location the users would not be able to see above [COLOR="#FF0000"]public[/COLOR] (e.g /srv/private) but any directory or file below would be available.
> 

And, this bit at the bottom here
```
[COLOR=#000000][FONT=Ubuntu Mono] 
      create mask = 0664
[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]force directory mode = 2775
[/FONT][/COLOR]
```

How is the permissions built up? I know the 0 in front of the 0664 shouldn't matter, but what do the numbers mean and how are they separated? 

See [here]("https://help.ubuntu.com/community/FilePermissions") for file and directory permissions.  For a good explanation of extended file attributes ( the leading 2 or 0 ) see [here]("http://www.zzee.com/solutions/unix-permissions.shtml#setuid").

---

