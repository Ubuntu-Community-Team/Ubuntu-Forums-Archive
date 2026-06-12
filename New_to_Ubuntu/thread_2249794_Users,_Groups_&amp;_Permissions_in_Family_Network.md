---
title: "Users, Groups &amp; Permissions in Family Network?"
date: 2014-10-24
forum: New to Ubuntu
---

### Post by 2CV67 on 2014-10-24
I have a Desktop PC & a Netbook, on which I am administrator but various family members have logins for occasional use.
They don't have any confidential items on my machines.
We all expect that the administrator (me) should be able to shift files & folders as required between the various accounts & machines (like in Windows) but in fact I keep bumping into permission issues.

How should I set things up to have maximum access to all their files without doing anything stupid?

Are new files always created with the same permissions?
Or is there some setting I have not found?

Should other users be part of my group, or should I be part of their group(s) or what?

Answers in GUI terms would be much prefered!

---

### Post by yancek on 2014-10-24
Which operating systems?  windows 8, Ubuntu 12.04 and 14.04?  Two computers sharing directories/files between computers networked or sharing/accessing directories/files on the same computer with multiple users?  Sharing from Linux to Linux on network, use nfs, Linux to windows samba.  Setting permissions on which type filesystem?   Can't be very specific with just the general information you posted.

---

### Post by sandyd on 2014-10-24
> **2CV67 said:**
> I have a Desktop PC & a Netbook, on which I am administrator but various family members have logins for occasional use.
They don't have any confidential items on my machines.
We all expect that the administrator (me) should be able to shift files & folders as required between the various accounts & machines (like in Windows) but in fact I keep bumping into permission issues.

How should I set things up to have maximum access to all their files without doing anything stupid?

Are new files always created with the same permissions?
Or is there some setting I have not found?

Should other users be part of my group, or should I be part of their group(s) or what?

Answers in GUI terms would be much prefered!
If you want to move their files between accounts on the same computer, 
By default, files are created as 664 in the home folder and folders as 775.

As a result, adding  yourself to their default group (provided that their default group/etc has not been tinkered with, all of the above assumes default behaviour) should instantly allow you to access their files.
Something like
```

sudo usermod -a -G *familyusername* *yourusername*
```

Note that some applications may set more restrictive permissions (ex 700, 755, etc) on files and folders which may not allow you to access that particular file/folder.

For shifting files between computers, right click the folder to be shared, and choose "share this folder". I only have one account on this computer so I dont know if you can share folders that are not owned by you. Make sure to set "allow others to create/delete" and "guest access" options appropriately. Also, Samba does not work with Windows HomeGroups, you will need to disable homegroups if you have that enabled in order to access SAMBA shares on windows machines.

If your absolutely bored, try looking at syncing all their files between computers using syncthing/btsync. It doubles as a nice backup in case something goes down.

---

### Post by bab1 on 2014-10-24
> **2CV67 said:**
> I have a Desktop PC & a Netbook, on which I am administrator but various family members have logins for occasional use.
They don't have any confidential items on my machines.
We all expect that the administrator (me) should be able to shift files & folders as required between the various accounts & machines (like in Windows) but in fact I keep bumping into permission issues.

How should I set things up to have maximum access to all their files without doing anything stupid?

Are new files always created with the same permissions?
Or is there some setting I have not found?

Should other users be part of my group, or should I be part of their group(s) or what?

Answers in GUI terms would be much prefered!
Are your Desktop and Netbook both Ubuntu?  Are the users accessing the your two machines remotely (via some other client) or locally ( via direct access),  Either way there are some things that will help you understand what is going on with permissions and file (and directory) ownership.

When using Ubuntu, all files and directories are created with this ownership structure:  *user:user-group:others*.  This means if the user **bab** creates a file or directory the ownership will be: bab:bab:others.  The permissions are, by default 0775 for directories and 0664 for files.  This means that the creator (*owner:user-group *) has read and write permissions for a file (66) and all others have read only (4) permissions.  When the creator  (*owner:user-group *) has read, write and eXecute permissions (77) and all others have read and eXecute permissions (5).  The significance of the eXecute bit important.   That bit is used to allow descending (traversal) and reading of the listings in the directory.

So as you can see the ownership needs to be manipulated and then the permissions will take care of themselves.  The simplest way to take care of this is by creating a file system branch outside of the */home directory* branch.  You then set the group ID inheritance to a common group that all users are part of such as: *user:**common-group**:others*.  If you don't set the inheritance the user will always create objects with the user:user-group as described above.

Typically if the data is access remotely (via Samba or NFS) the location of the data is /srv.  This can also be accessed by multiple users of the machine directly. 

This can't be done using the GUI.  It's really simple using the terminal.  I do this several times a week when helping others.

Do you want help doing this via the terminal?

---

### Post by 2CV67 on 2014-10-25
Thanks for your several replies!

I was not specific enough at first.
My machines are described in my signature, which I just updated:
-Desktop with W8 & Ubuntu 14.04.1
-Netbook with W7 & Ubuntu 14.04.1
Users access each machine directly & they are both on a Wifi LAN, but also use USB sticks & USB Hard-Drives for backups & transfers.
Windows is only for stuff Ubuntu can't do, like updating TomTom GPS etc.

Mainly I am interested in file-sharing Ubuntu-Ubuntu.

It would be a good start if I could get that working cleanly between accounts on one machine first, before dealing with the further complications of Samba! 

I am not attracted (yet) by the idea of creating a special file-system branch or by learning to do complex stuff by terminal (but thanks for the offer!).
I am a die-hard GUI user (see signature) and want to believe that simple file-sharing must be possible without extravagant tactics!

I will try adding myself to the other users' groups & see how much that helps.

Thanks again for all your input!

---

### Post by 2CV67 on 2014-10-25
OK - a concrete example:

I just tried to push an image file from my account (A) to a family member account (B) with no success.
I tried dragging/dropping between 2 nautilus windows from Public folder (A) to Public folder (B).
No result.
Same with Copy/Paste (no Paste option appears in B).

I added myself to B group - no change.
Reboot - no change.

Looking at the permissions of B Public folder, I see "create/delete  - access - access".
I changed that to "create/delete - create/delete - access".

Now I can shift files to & from B Public folder.

Is that what I should have done?

I didn't use "Change permissions for enclosed files".
Should I?
What is the exact effect?

---

### Post by 2CV67 on 2014-10-25
More digging:

When I create a new file or directory, it gets the expected permissions of 664 & 775.
But all the non-new files & directories in my home seem to be 600 & 700...

I am guessing this is because of their history.
They have been backed-up to an external hard drive with Grsync, then pulled into my fresh installation of 14.04.1 by drag & drop.
Can that explain 600 & 700?

In the settings for Grsync, I have NOT checked "Preserve owner / Preserve permissions / Preserve group".
Should I have done?
What are the implications of yes & no there?

Is there a SAFE way of resetting these permissions?
By GUI?

Complicated business...

---

### Post by 2CV67 on 2014-10-25
Ever onward...

I set permissions in my home directory to 664 & 775.
I did this the laborious GUI way, in Nautilus > Properties for each directory & using the button to "Change permissions for enclosed files".
I know chmod would be much quicker, but I wanted to avoid some directories (hidden & others) so I did it my way...

Obviously I have not checked every file, but a random check looks OK.

Then I tried Grsync on a test directory, but this time I checked all the boxes for Preserve Owner, Group & Permissions.
Surprise, surprise!
On the External Hard Drive, the permissions are back to 600/700!

Suggestions welcome!

---

### Post by 2CV67 on 2014-10-25
On my EHD, creating a new directory results in 700 permissions & cannot be changed.

I checked back on 2 EHD's I had used with my previous PC which ran Ubuntu 14.04 before it died in August.
They were used to backup the same home directory & to initially fill my new PC's home directory.
One had 664/775 permissions & the other had 600/700.

The good one is formatted ext3 & the bad one NTFS.

The 2 new EHD's I use with my new PC are both NTFS.

Voila!

So now I just need to reformat them to ext4.

I suppose this sort of detail is explained somewhere, but I certainly missed it when I spent a long time agonising between FAT32, NTFS & ext3/4 for my EHD's!
Grrr!!!

---

### Post by yancek on 2014-10-25
> Then I tried Grsync on a test directory,

Did you move/copy files to the test directory on the external drive?  If so, where (into what directory) did you copy them and what are the permissions on that directory?

> I tried dragging/dropping between 2 nautilus windows from Public folder (A) to Public folder (B).

In that case user A would need write permisisons in the B folder, be in the group for that folder and have write permissions.  Or you could use sudo or gksu nautilus to open a file manager.  I'm not really sure what you are doing.  Usually when people want to have a shared directory, they create a separate partition and add users to whatever group they all belong to and give the group write permissions.  It seems like you are trying to give different users write permissions to every user /home directory.  If that's the case, then there is no point in creating separate users, just create one user and give everyone the password.  Maybe you could clarify a little what exactly you want.  Having separate user directories is the default on Linux with only the user and root having write permissions.

---

### Post by 2CV67 on 2014-10-26
I reformatted the EHD to ext4 using, naturally, Gparted.
After that, I could not even create a new folder in the EHD.
It was owned by Root!

I saw a lot of forum threads on this subject, so apparently it is not just me.
There were a lot of solutions involving chown which I don't fancy.
I tried gksudo nautilus but that refused the ownership change, then crashed.
I tried reformatting the EHD again, using the Disks application from the Dash & that worked OK, so I now have control of my EHD again.

A new backup to that EHD shows all files & directories keep their original permissions.
Phew!
Whatever happened to "It just works"?

I looked again at threads talking about suitable formats for backups, and mostly they say NTFS is a reasonable choice...
That seems wrong to me.

---

### Post by 2CV67 on 2014-10-26
> **yancek said:**
> It seems like you are trying to give different users write permissions to every user /home directory.  If that's the case, then there is no point in creating separate users, just create one user and give everyone the password.  Maybe you could clarify a little what exactly you want.

What I want is to be able to control my machines as I imagine an administrator can.
Remembering that this is just family on a domestic LAN.
I want to be able to pull & push files between predefined users and for the files to be usable by those users.
Between users on each machine & between machines on the LAN.
I want each user to have his own desk (login) & keep his own data separate from the others for convenience, but not hermetically.
I don't want other users to have sudo rights.

When I started this thread, I didn't realize that part of my problem was that my home folder contents had the wrong permissions, due to having been recovered from a backup on a drive formatted NTFS.
Now I do.
That is progress.

I think another part of the necessary solution is to have all users in each others' groups, so transfered files can be worked on when received, but I am not so sure about that yet...
But I do want to avoid having to set file permissions on a case-by-case basis - I want it to work with any created or imported files.

---

### Post by 2CV67 on 2014-10-26
OK, I now have file-sharing working OK between accounts on same PC.
(To get there, I had to correct the wrong permissions inherited from my NTFS backup drive, then include users in each other's groups.)

I also have file-sharing working between my own accounts on 2 PC's via the LAN.
I got there with Nautilus > Public folder > Properties > Local Network Share > Tick all boxes > Modify Share.
I then accepted the offer to change permissions (777!)...
I put myself in the Sambashare group, but am not sure if that was needed or not.
Anyway, I can now see my Public folders accross the LAN & shift files between them OK.

Next step is to get another user's (B) Public file shared & there I am stuck at the moment.
First I went into B account & tried the same procedure as above.
Not surprisingly, I got a refusal:
```
'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error Permission denied 
You do not have permission to create a usershare. Ask your administrator to grant you permissions to create a share.

```
So I went to Users & Groups > Advanced > User Privileges
and ticked 'Share files with the local network'.
B is already part of the sambashare group.
After that change, I now get this error:
```
'net usershare' returned error 255: net usershare add: failed to add share public. Error was Operation not permitted
```

And that is where I am stuck at the moment - trying to get user B's Public folder shared.

Ideas warmly welcomed!

---

### Post by 2CV67 on 2014-10-27
Still stuck in the same hole as yesterday.

Put simply:
Acting as an ordinary user B (not administrator) I want to share B's Public folder as simply as possible by GUI.
I right-click the folder > Properties > Local Network Share > Share this folder + Allow others + Guest access > Create Share.

But I get this error:
```
'net usershare' returned error 255: net usershare add: failed to add share public. Error was Operation not permitted
```

B is in sambashare group & has Privileges including:
- Connect to wireless...
- Share files with local networks

If I try to share B's Public folder whilst operating as myself A (administrator) I get a different error:
```
'net usershare' returned error 255: net usershare add: cannot share path /home/B/Public as we are restricted to only sharing directories we own.
	Ask the administrator to add the line "usershare owner only = false" 
	to the [global] section of the smb.conf to allow this.
```

Maybe that error contains the solution (?) but I am trying to do all this without having to dig into configuration files.

Is it impossible?

---

### Post by yancek on 2014-10-27
> I then accepted the offer to change permissions (777!)...

That would give anyone with physical access to the machine, including your cat, the ability to delete anything in that directory or its sub-directories.

> 'net usershare' returned error 255: net usershare add: failed to add share public. Error was Operation not permitted

Which would indicate you need administrator permissions to do it.

> If I try to share B's Public folder whilst operating as myself A (administrator) I get a different error:

Just being logged in as user A which has administrative rights doesn't mean you have them.  Your user is also a normal user.  The sudo thingy is a bit schizophrenic as you can log in as user A and be a normal user or log in to a terminal and use sudo and then have administrative rights.  gksu natuilus should prompt you for user A password and after correctly entering it, you will have root privileges. 

The permissions in the directory you are copying "to" are the determining factor rather than from.  User B with read privileges on a user A account can copy from user A directory to user B directory whereas user A cannot copy "to" user B directory unless user A also is logged with root permissions.

In an earlier post, you indicated that you priority was sharing between Linux systems so I'm wondering why you are using samba which is designed to share from Linux to windows.  Sharing between Linux systems on a local network is usually done with nfs (network file system).  I don't use samba but I guess it could work

---

### Post by bab1 on 2014-10-27
> **yancek said:**
> ... using samba which is designed to share from Linux to windows.  Sharing between Linux systems on a local network is usually done with nfs (network file system).  I don't use samba but I guess it could work
Samba is really just a userspace virtual file system much like [FUSE]("http://fuse.sourceforge.net/").  It will work with Windows, MAC OSX and Linux.  The distinctive feature is that you can browse for shares rather than having to specifically configure the mounting as in NFS.

---

### Post by chopra on 2014-10-30
> **2CV67 said:**
> What I want is to be able to control my machines as I imagine an administrator can.
Remembering that this is just family on a domestic LAN.
I want to be able to pull & push files between predefined users and for the files to be usable by those users.
Between users on each machine & between machines on the LAN.
I want each user to have his own desk (login) & keep his own data separate from the others for convenience, but not hermetically.
I don't want other users to have sudo rights.

When I started this thread, I didn't realize that part of my problem was that my home folder contents had the wrong permissions, due to having been recovered from a backup on a drive formatted NTFS.
Now I do.
That is progress.

I think another part of the necessary solution is to have all users in each others' groups, so transfered files can be worked on when received, but I am not so sure about that yet...
But I do want to avoid having to set file permissions on a case-by-case basis - I want it to work with any created or imported files.


Ughh!  What a mess of a thread!  Okay, so what about having a shared directory, where everyone has write permission, and making it a restricted deletion directory (i.e. set the "sticky bit" to the directory.) ?  Then users can move or copy their own files there, make their own copies of someone else's files, and not be able to delete someone else's files?  Wouldn't that just be simpler than doing all of this extra work?  As far as multiple machines, having a corresponding directory on those machines would allow remote copying, wouldn't it?

Chopra

---

### Post by 2CV67 on 2014-10-30
I agree this is a mess of a thread!

It reflects the mess I have been in for several reasons, not all of which are total stupidity or inability to read instructions (though some may be!).

Somebody asked why I chose to use Samba.
I didn't choose to use Samba.
I chose the file-sharing option offered in Nautilus, assuming it would be the simplest. ([http://www.howtogeek.com/116309/use-ubuntus-public-folder-to-easily-share-files-between-computers/](http://www.howtogeek.com/116309/use-ubuntus-public-folder-to-easily-share-files-between-computers/))...
Opting to share, say, the Public Folder (you could be forgiven for expecting the Public Folder to already be, well, you know - Public, couldn't you?) anyway, opting to share it, automatically drags in Samba, which was already present after installing Gimp.

So my current problem is simply that I can't get another user's Public Folder to be shareable (whether I try to do it from Administrator's account or other user's account) as explained in my previous post.

I assume this is normally possible & that must be doing something wrong, but what?

---

### Post by chopra on 2014-11-03
> **2CV67 said:**
> I agree this is a mess of a thread!

It reflects the mess I have been in for several reasons, not all of which are total stupidity or inability to read instructions (though some may be!).

Somebody asked why I chose to use Samba.
I didn't choose to use Samba.
I chose the file-sharing option offered in Nautilus, assuming it would be the simplest. ([http://www.howtogeek.com/116309/use-ubuntus-public-folder-to-easily-share-files-between-computers/](http://www.howtogeek.com/116309/use-ubuntus-public-folder-to-easily-share-files-between-computers/))...
Opting to share, say, the Public Folder (you could be forgiven for expecting the Public Folder to already be, well, you know - Public, couldn't you?) anyway, opting to share it, automatically drags in Samba, which was already present after installing Gimp.

So my current problem is simply that I can't get another user's Public Folder to be shareable (whether I try to do it from Administrator's account or other user's account) as explained in my previous post.

I assume this is normally possible & that must be doing something wrong, but what?

Hmmm,
I'm rather new to Ubuntu myself.  I'm not sure if this will help or not, but when I transfer files between machines, I always use the command shell, using an scp, ssh, or sftp command.  Can you set up an ssh connection between machines?  You said that there are multiple machines, I'm not sure how they're connected.  Are the user accounts independent on each (i.e., do people have to change passwords on every machine, and did you create user accounts on each machine separately?)

Chopra

---

### Post by 2CV67 on 2014-11-04
Thank you for your input, but we must be a long way apart in philosophy!

I have enough cans of worms open without diving into scp, ssh or sftp.
I just want simple GUI stuff.

My questions at the moment are:
1. Can non-admin user share a folder with Nautilus/Samba?
2. How?
3. If my attempts are giving me error 255: Operation not permitted, then what can I do to diagnose the reasons for this error.

Thanks!

---

### Post by chopra on 2014-11-16
> **2CV67 said:**
> Thank you for your input, but we must be a long way apart in philosophy!

I have enough cans of worms open without diving into scp, ssh or sftp.
I just want simple GUI stuff.

My questions at the moment are:
1. Can non-admin user share a folder with Nautilus/Samba?
2. How?
3. If my attempts are giving me error 255: Operation not permitted, then what can I do to diagnose the reasons for this error.

Thanks!

I see no one else has responded yet. I'm a bit out of my depth with GUI as I rely very heavily on the command line. the three commands I listed are extremely simple to learn, and there's bound to be other instances where you will need to rely on the command line.  If you're looking for just "simple GUI stuff", I'm afraid Linux may not be the right operating system for you, as a lot of functionality comes from the command shell.

As for your questions, I'm afraid those are beyond the scope of my knowlegde.

Chopra

---

