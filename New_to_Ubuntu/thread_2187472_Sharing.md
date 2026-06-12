---
title: "Sharing"
date: 2013-11-12
forum: New to Ubuntu
---

### Post by neil5 on 2013-11-12
What is the deal with sharing folders?

I want to share a folder with another Ubuntu 13.10 user on the same computer. I've shared the folder and chose the option that requires a password to access the shared folder via the network browser (Allow others to create and delete files in this folder). When I try to open the folder from another login I'm asked for a username, workgroup and password. I entered the creators username and password and the dialog box just keeps coming back, as if to say - incorrect details. I cannot even open the shared folder via the network browser whilst logged into the correct user account (the owner).

I've added all users to the same group as the folder. I've done this using the Users and Groups app (Gnome-System-Tools).

Also, worth noting...I'm doing all this from inside VirtualBox on a Windows 7 machine, although I seem to be having issues on my laptop also, that has Ubuntu 13.10 installed directly on the hard drive, and nothing else.

Any ideas?

Thanks.

---

### Post by TheFu on 2013-11-12
Network sharing is different from local sharing.
Local sharing is 100% groups and permissions - no need for samba, NFS.  Google "ubuntu file directory permissions" to learn how.

Network sharing is meant for users on different workstations. UNIX/Linux to each other is best done with NFS.  It is also based on users/groups managed between the machines.  The same file/directory permissions learned for local directory sharing works under NFS.

If you have 2 different VMs under virtualbox, use network sharing - but both systems must be running concurrently for access to work.

If you can't find thee tutorial ask and I'll look for it again.  Found it a few hrs ago easily.

---

### Post by neil5 on 2013-11-13
Thanks for the reply TheFu.

So if i give the folder i want to share, the correct permissions, how does the other user find that folder? Users can't access other user's profiles can they?

---

### Post by Lars Noodén on 2013-11-13
By default, they can read each other's folders.  It also looks like it is possible to read each other's files, too.  I'm kined of surprised at that default.  That's easy to fix, but should not have been the default, in my opinion.

Anyway, it is just to navigate up into /home and then back down again into the right folder.

---

### Post by neil5 on 2013-11-13
Wow, i feel fairly stupid now lol. 

I guess the next question is, how do i sort this out? Is it just a case of assigning permissions to each user's folder to deny access??

---

### Post by Lars Noodén on 2013-11-13
Yes, it's just a matter of setting permissions for the top folders.  That will exclude access for the subfolders then.  

```

sudo chmod 750 /home/*

```

If you want to be thorough you should also set the umask from 0022 to 0027 or 0077 in .profile

---

### Post by TheFu on 2013-11-13
Don't feel stupid.  If you've never worked in a team environment, how would you know?

Everywhere that I've worked, shared-team directories were NOT in HOME dirs.  We always setup a shared area elsewhere ... usually on NFS mounted storage ... but that isn't important. I was lucky and learned in an expert lab environment with people who had 15+ yrs of UNIX experience.

The last question really means it is time to work through a good file/directory permissions tutorial.  Learn all about the chmod options. Read up on newgrp, id, etc.... It is amazing the sort of permissions you can provide with just those.  You need to spend the time learning it - lots of references exist .. google, youtube, ... paid training (no needed).  If we told you the exact answer now, it is not "teaching you to fish" and you'll be back over and over.

You can allow people to write to a directory, but not read it, for example .... or read the files, but not get a file list (so they only access the file you provide them).  If that doesn't cover everything you need, then there are ACLs (man facl).  I have never needed to use ACLs ... in 20+ yrs.

When you are all done, you'll need sudo much less and will understand why sudo and the GUI versions should almost **never** be used to run any GUI tools. They screw with file permissions that you dno't want touched.

---

### Post by Morbius1 on 2013-11-13
OK, I'm confused.

** By default all users have read access to each others folders.

** If you want write access you need to change permissions to 775 on the folder you want shared ( assuming you have changed the group of that folder to one both users have membership.

** The real problem is what you mean by "write". 

With permissions of 775 userB can add to ( a directory write ) and even delete a file owned by userA but he can't edit a particular file unless it's his own. The old way of fixing this is to set the sgid bit on the folder so that every file is saved with the group of the parent folder but it requires that the default umask is set to 002 so files are saved with permissions of 664 not 644. 

And that is now a problem in 13.10 because of this bug since the override sets umask to 022: [Upstart overrides the user's umask]("https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/1240686")

There are 43 different locations ( that might be a slight exaggeration ;-) ) where you can set a default umask, one more incoherent than the next, and all of them will be ignored until this bug is fixed. Bindfs can be used to overcome this problem or the user can wait until the bug fix is released.

---

### Post by neil5 on 2013-11-13
Thanks, I'll look into this.

---

### Post by TheFu on 2013-11-13
> **Morbius1 said:**
> OK, I'm confused.

** By default all users have read access to each others folders.

** If you want write access you need to change permissions to 775 on the folder you want shared ( assuming you have changed the group of that folder to one both users have membership.

** The real problem is what you mean by "write". 

With permissions of 775 userB can add to ( a directory write ) and even delete a file owned by userA but he can't edit a particular file unless it's his own. The old way of fixing this is to set the sgid bit on the folder so that every file is saved with the group of the parent folder but it requires that the default umask is set to 002 so files are saved with permissions of 664 not 644. 

And that is now a problem in 13.10 because of this bug since the override sets umask to 022: [Upstart overrides the user's umask]("https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/1240686")

There are 43 different locations ( that might be a slight exaggeration ;-) ) where you can set a default umask, one more incoherent than the next, and all of them will be ignored until this bug is fixed. Bindfs can be used to overcome this problem or the user can wait until the bug fix is released.

**When it comes to file/directory permissions and HOME dirs, it is not safe to assume any defaults ... ever.** There may or may not be read permissions. Morbius's point is true. There are many reasons to setup all sorts of different and even strange permissions in HOME.  The only way to know what permissions exist is to completely, fully, understand file and directory permissions.  There are times with the sgid/suid/and sticky bits make sense, but those don't happen all that often for a normal user.  I've never needed to use bindfs .... er ... ever. I suppose it might be nice if you have sensitive data higher in a directory system than you'd like.

The point about umask is extremely true also. At home, I use a more restrictive umask then at work with my team.  Further, at work, I remove the stupid default uid/uid groups and have a "users" group for every user. After all, we need to share by default. If a user doesn't want to share, they can change their umask or manage dir/file permissions manually and **** off the team lead. Different project teams will have a groupid for them to share files and the project will purchase primary and backup storage just for their team.  

I remember being hassled all the time from my team members when I was new. I was either overly permissive or too restrictive.  The badgering was good - it forced me to learn, which made me more secure.

After, the root of all security on Linux/UNIX is based on these same file and directory permissions. Understanding is a must.

---

### Post by Morbius1 on 2013-11-13
Here's a mini HowTo on the use of Bindfs is you are interested:

Try the following experiment to see how this works:
[1] Install bindfs
```
sudo apt-get install bindfs
```
[2] Create a couple of Test directories

*** Create a hidden directory:
```
sudo mkdir /.Test
```
*** And an non-hidden directory:
```
sudo mkdir /Test
```
*** Use bindfs to mount one to the other:
```
sudo bindfs -o perms=0660:+X,force-group=plugdev /.Test /Test
```
Now copy a file to /Test. It's permissions will be 660 and it's group will be plugdev. To undo the mount:
```
sudo umount /Test
```
[COLOR=#0000cd]* Note: The only reason I chose plugdev as the group is that it's already available.*[/COLOR]

To make this permanent you have a couple of options:

*** Add the line without sudo to rc.local
*** Or, Add a line to /etc/fstab with a different syntax:
```
bindfs#/.Test    /Test    fuse    perms=0660:+X,force-group=plugdev    0    0
```
*** Or, The way I do this is with an Upstart Job which is in my opinion  the most reliable and safest way to do these sorts of things:

_*Create an upstart file:*_
```
gksu gedit /etc/init/bindfs-mounts.conf
```
_*With this content:*_
```
# Remount Directories with Bindfs
#
description "Bindfs Remounts"

start on stopped mountall

script
bindfs -o perms=0660:+X,force-group=plugdev /.Test /Test
end script
```
Once set by bindfs all files and folders created in, copied to, or moved to that folder will have group ownership of plugdev and folder/file permissions of 770/660 except for files that are executable - they will be 770. At this point no other process - not umask, not Samba, not even root - can change permissions on an individual file.

---

### Post by TheFu on 2013-11-13
> **Morbius1 said:**
> Here's a mini HowTo on the use of Bindfs is you are interested:

That is some cool stuff for admins!  Guess we know how mount.ntfs works now (which drives me nuts) ... it uses bindfs.
Still, I can see uses and simplified methods from the way I've been doing things in some places.  

Plus it will be lots-o-fun to screw with development teams. Never let them create an executable file (ok, just not set the +x perms) on their file system - I can hear the laughing now! ;)  Wonder how much time they will waste on this? It would be cruel.

---

### Post by Morbius1 on 2013-11-13
That's a big "X" in the bindfs statement. Files that are executable will remain so. It's the same as doing a:
```
chmod -R a+rwX,o-w /Test
```
I'll edit my previous post to make that clear.

---

### Post by TheFu on 2013-11-13
> **Morbius1 said:**
> That's a big "X" in the bindfs statement. Files that are executable will remain so. It's the same as doing a:
```
chmod -R a+rwX,o-w /Test
```
I'll edit my previous post to make that clear.

Saw that ... it was clear to me, but I was thinking of a different use-case:  "Screw with devs" was the purpose. ;)  Might be handy on a data file system too - you know, a place for documents and media files only.

Some day I'll grow up ... maybe around age 60?  Probably not.

---

### Post by Morbius1 on 2013-11-13
You know, the subject of the execute bit and bindfs is somewhat confusing especially if you've never used it before so it might be worth explaining a bit more.

Bindfs creates a "view" of a folder whose attributes are defined by the bindfs statement. It has no affect on the folder that it is bound to. So using my example above if I create a new file in /Test in 13.10 it will save with permissions of 644 in /.Test but it will appear as 660 in /Test because bindfs makes it so.

Similarly, if I set the execute bit on that file in /Test it will change it to executable in /.Test but this time also in /Test since the bindfs statement makes it so with the "perms=0660:[COLOR=#0000cd]**+X**[/COLOR]" statement.

So setting the execute bit in bindfs can be thought of as working as designed because of the way I crafted the bindfs statement or the exception to the "no other process can change permissions" rule.

---

### Post by petersfreeman2 on 2013-12-27
I have a home network where my wife and I are members of the network.  We each have our own desktops and on her machine, I have set her up as owner=mary and group=family.  On my machine owner=peter, group=family.  I created the family group and added mary and peter as members.  Next I set umask 007 (or 0007) in the files:       ~/.profile    ~/.bashrc     /etc/profile     /etc/login.defs     Both my wife and I backup our files using rsync to a backup drive attached to my machine and formatted EXT4 and is shared.  The problem I am having is some files end up on that external drive with the original default permissions of rw-r--r-- instead of rw-rw---- and in the case of folders some end up with the original default permissions of rwxr-xr-x instead of rwxrwx---  In addition, some of my files end up as peter:peter instead of peter:family and her files end up as mary:mary instead of mary:family  I am forever running chown  and chmod so either of us can access the others files.  when I type umask in a CLI I get 0022.  I am not sure why this is happening.  My research on umask has not brought up any areas that I need to adjust.  my latest effort is to add sudo chfn -o "umask=007" peter to my /etc/passwd file and sudo chfn -o "umask=007" mary to my wife's.  Not sure if this is the right thing to do as the /etc/passwd file contains lines that are not like the commands I added.  Any ideas?  Thanks, Peter

---

