---
title: "working directory for programs run from dash"
date: 2013-11-08
forum: New to Ubuntu
---

### Post by greatkingrat2 on 2013-11-08
How do I find/set the working directory for programs run from Unity Dash?

Here's my scenario:
I have two hard drives. An SSD mounted at / and a HD mounted at /media/HD1.  I created a folder called home on the HD, copied /home to that folder, and then changed /home to be a symlink to /media/HD1/home. Almost everything works.

Programs run from the Dash (I think that's the term for the search button) get started with a working folder /media/HD1/home/user rather than /home/user.  it's effectively the same thing, but not exactly correct.

What did I do wrong? How do I fix it? (My googling searches result in changes to .bashrc and the like, which isn't executed for other programs...)

---

### Post by fantab on 2013-11-08
When you copied /home to your/media/home you've also copied .(dot)folders and files to /media/home and then created a symlink. 
Now, .folders/files store application data and preferences/settings in those hidden .folders/files.

IMO its a bad idea to keep you dot(.)folders/files on /media/home. Instead of copying the whole of /home folder to /media/home, copy only YOUR data folders, like Documents, Downloads, Pictures etc. then create Symlinks of data folders in /home. Leave .folders/files in /home and DON'T copy them to /media/home

You can change the default /save/path of applications to point to your /media/home. For instance, Libreoffice Writer, by default, saves documents to /home/Documents, you will change the default /save/path to /media/home/Documents. Since you have made symlink from /media/home/Documents in /home you can access your saved document from /home/Documents. Similarly you can change the default /save/path of Applications you use to /media/home/'relavant directory'.

I hope I have understood you correctly, is this what you were looking for?

---

### Post by greatkingrat2 on 2013-11-08
That isn't really what I was looking for.  That results in a lot of symlink management for myself and other users as well as preference management for myself and other users.

I want all home folders on the HD and I want them in a subdirectory (which is why I don't think I can mount the hard drive directly as /home).  And since hard links can't cross drives, a symlink seemed like the way to make /home point to /media/HD1/home.

---

### Post by ian-weisser on 2013-11-08
It seems like you wan to have a separate /home partition.
The link method seems needlessly complex. What's the advantage of linking it instead of the usual method of defining it in /etc/fstab so it gets automatically mounted?

---

### Post by greatkingrat2 on 2013-11-08
I should add that my account home directory in /etc/passwd is /home/user, not /media/HD1/home/user

---

### Post by greatkingrat2 on 2013-11-08
The HD/partition is automatically mounted in fstab, just as /media/HD1 rather than /home.

I did that because I wanted all the home folders to be on the hard drive as subfolders of one folder on the HD.  Mounting it as /home puts all the home folders as /home/user1 /home/user2. If I pull the hard drive and take it to another computer, I want the directories listed to be home, not user1 user2 etc.

---

### Post by deadflowr on 2013-11-09
Look into the file /home/user/.config/user.dir.dirs and the changes you could make there as a possible solution.
 Maybe helpful, maybe not
[http://askubuntu.com/questions/29671/functions-of-xdg-user-dirs](http://askubuntu.com/questions/29671/functions-of-xdg-user-dirs)

---

### Post by greatkingrat2 on 2013-11-09
> **deadflowr said:**
> Look into the file /home/user/.config/user.dir.dirs and the changes you could make there as a possible solution.
 Maybe helpful, maybe not
[http://askubuntu.com/questions/29671/functions-of-xdg-user-dirs](http://askubuntu.com/questions/29671/functions-of-xdg-user-dirs)

In ~/.config/user.dir.dirs is set to stuff like XDG_DESKTOP_DIR="$HOME/Desktop"
In /etc/xdg/user.dir.dirs, they are DESKTOP=Desktop

Neither references /media/HD1.  

grepping all files in /etc tree for /home/HD1 , there's a line in mtab that says:
gvfsd-fuse /media/HD1/home/user/.gvfs fuse.gvfsd-fuse rw,nosuid,nodev 0 0

Could that be the source of it?

---

### Post by bab1 on 2013-11-09
> **greatkingrat2 said:**
> In ~/.config/user.dir.dirs is set to stuff like XDG_DESKTOP_DIR="$HOME/Desktop"
In /etc/xdg/user.dir.dirs, they are DESKTOP=Desktop

Neither references /media/HD1.

The individual users specs are at: /home/$USER/.config/user-dirs.dirs  You can also use UbuntuTweak Admins>>User Folder to set them. 
> 

grepping all files in /etc tree for /home/HD1 , there's a line in mtab that says:
gvfsd-fuse /media/HD1/home/user/.gvfs fuse.gvfsd-fuse rw,nosuid,nodev 0 0

Could that be the source of it?
You shouldn't be using /media for this at all.  This directory is for auto mounting removable media.  That's why you are seeing gvfsd-fuse.  There are several ways to accomplish what you want.  One way would be to mount the HDD at /home.  This way any users that log in have there data on the HDD.  As you noted you can change where your home directory is located, but I don't see any reason to do that if all you want to do is have all the home dir data on the HDD.  Whatever you do, don't use /media for this purpose.

---

### Post by greatkingrat2 on 2013-11-09
> **bab1 said:**
> The individual users specs are at: /home/$USER/.config/user-dirs.dirs  You can also use UbuntuTweak Admins>>User Folder to set them. 

You shouldn't be using /media for this at all.  This directory is for auto mounting removable media.  That's why you are seeing gvfsd-fuse.  There are several ways to accomplish what you want.  One way would be to mount the HDD at /home.  This way any users that log in have there data on the HDD.  As you noted you can change where your home directory is located, but I don't see any reason to do that if all you want to do is have all the home dir data on the HDD.  Whatever you do, don't use /media for this purpose.

It was mounted in /media when it came from system76.  What sequence of commands should I be running to do this properly that accomplishes the following:

1. puts the user folders on the secondary hard drive.
2. allows me to have the HD as one partition (I don't like managing partitions)
3. keeps the user folders on the HD separate from other folders

If I mount it in fstab as /home, I can't do 3 unless I don't get 2.  Unless I'm missing something.  I really don't care if the drive is mounted in /media.  That's just where it was mounted when I got the machine.

---

### Post by deadflowr on 2013-11-09
> **greatkingrat2 said:**
> In ~/.config/user.dir.dirs is set to stuff like XDG_DESKTOP_DIR="$HOME/Desktop"
In /etc/xdg/user.dir.dirs, they are DESKTOP=Desktop

Neither references /media/HD1.  

grepping all files in /etc tree for /home/HD1 , there's a line in mtab that says:
gvfsd-fuse /media/HD1/home/user/.gvfs fuse.gvfsd-fuse rw,nosuid,nodev 0 0

Could that be the source of it?

[gvfs]("http://en.wikipedia.org/wiki/GVFS") 
Though I don't think that has much to do with what you're dealing with.

As far as the users.dir.dirs files go, I point those to you simply as something you can look into and investigate.

I really don't know the unconventional way you've set your system up, so any advice beyond pointing toward possibly useful information might cause problems. 

My only real question would be, what programs do you have in your home folder? And with that, why do you need to input the full path in the dash to launch them?

Edit: Don't take my stating it as unconventional as either wrong or bad, simply take it as different from the norm.

---

### Post by greatkingrat2 on 2013-11-09
> **deadflowr said:**
> 
My only real question would be, what programs do you have in your home folder? And with that, why do you need to input the full path in the dash to launch them?

I have no idea what you are talking about with respect to needing to input the full path.  I don't want to input a full path.

---

### Post by greatkingrat2 on 2013-11-09
> **bab1 said:**
> Whatever you do, don't use /media for this purpose.

This page: [https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive) says: 
> [COLOR=#333333][FONT=Ubuntu]Now that the drive is partitioned and formatted, you need to choose a mount point. This will be the location from which you will access the drive in the future. I would recommend using a mount point with "/media", as it is the default used by Ubuntu. For this example, we'll use the path "/media/mynewdrive"
[/FONT][/COLOR]
I'm really confused now.  Where is this hard drive supposed to be mounted?

---

### Post by bab1 on 2013-11-09
> **greatkingrat2 said:**
> It was mounted in /media when it came from system76.  What sequence of commands should I be running to do this properly that accomplishes the following:

1. puts the user folders on the secondary hard drive.
2. allows me to have the HD as one partition (I don't like managing partitions)
3. keeps the user folders on the HD separate from other folders

If I mount it in fstab as /home, I can't do 3 unless I don't get 2.  Unless I'm missing something.  I really don't care if the drive is mounted in /media.  That's just where it was mounted when I got the machine.
The drive should not be thought of as a secondary drive.  In Linux you can mount a partition with a file system to the root file system ( / ) at any point (i.e. /srv or /data or /home).   The device (the HDD) can be a single partition with an ext4 file system.  You mount it either via the /etc/fstab file. This configures the mount command that is issued at boot up time.  Here is the line in my /etc/fstab the mounts a partition like I described```

#   <file system>                            <mount point>      <type>  <options>  <dump>  <pass>
# /home was on /dev/sdb1 during installation
UUID=46a258bf-6ace-4d52-b4d7-db47e7b3de7b      **/home **          ext4    defaults        0       2
```
The fields in the line are listed in the first line starting with the #

To partition the device (HDD) you can use *parted* at the CLI or *gparted* with a GUI interface.  See ```
man parted 
```...here is some [more info]("https://www.google.com/search?q=linux+partitions+parted+or+gparted&btnG=Go!") about parted and gparted.

Then you add the file system to the partition.  See here: [https://help.ubuntu.com/community/InstallingANewHardDrive]("https://help.ubuntu.com/community/InstallingANewHardDrive") and here: [http://ubuntuserverhelp.com/using-mkfs-to-create-a-file-system/]("http://ubuntuserverhelp.com/using-mkfs-to-create-a-file-system/").  With the GUI you can also use *disk utility* to do this.

Once you have done these 2 items you have to add the line to the fstab file and issue the mount command to mount the partition.

Is this detailed enough for you to just dive in and do it.  I think not.  Read the material and ask more questions.  You need to understand the basics of this.  I think the @oldfred is the most versed in teaching newbies how all of this is done.  So you might ask hime for some help.  I do this all the time but I don't think about it in terms of instructing someone.  Who knows what I may leave out of the description.

Although you may not care about where the drive is mounted, there are still valid reasons to NOT mount it at /media.  It cam that way because it's a USB HDD and lowest common use is as a removable disk.  The way you want it really is not considered a removable device even if it physically is removable.  Mounting it by fstab makes it part of the filesystem even if it is external and can be unmounted and detached.

Questions?

---

### Post by bab1 on 2013-11-09
> **greatkingrat2 said:**
> This page: [https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive) says: 

[/FONT][/COLOR]
I'm really confused now.  Where is this hard drive supposed to be mounted?

There are subtleties to all of this.  If you are just going to plug the usb drive in and have it work, it will be mounted at /media.  If you are mounting the drive and you want consistent parameters then you want to define them and NOT mount the drive at /media.  In other words /meda is for auto mount and /home is where you would mount the drive for seamless operation in the typical Linux file system hierarchy. 

The 2 operations use the same hardware but not the same setup.  In addition you probably do not want to use fdisk.  The more modern partitioning software is parted (gparted).

---

### Post by greatkingrat2 on 2013-11-09
> **bab1 said:**
> 
Is this detailed enough for you to just dive in and do it.  I think not.  Read the material and ask more questions.  You need to understand the basics of this.  I think the @oldfred is the most versed in teaching newbies how all of this is done.  So you might ask hime for some help.  I do this all the time but I don't think about it in terms of instructing someone.  Who knows what I may leave out of the description.

Although you may not care about where the drive is mounted, there are still valid reasons to NOT mount it at /media.  It cam that way because it's a USB HDD and lowest common use is as a removable disk.  The way you want it really is not considered a removable device even if it physically is removable.  Mounting it by fstab makes it part of the filesystem even if it is external and can be unmounted and detached.

Questions?

It's not a USB hard drive.  It's an internal hard drive.

And I even understand how fstab works generally.  I spent several hours reading the man page and googling it. (I don't get some of the arcane options, but I do understand how it works generally.)

If I mount the HD at /home, and user directories are created underneath it, that essentially means I can only put user directories on the HD.  I want to have other things on the hard drive. Is the only way to do that to partition the hard drive into two partitions?

---

### Post by bab1 on 2013-11-09
> **greatkingrat2 said:**
> It's not a USB hard drive.  It's an internal hard drive.

And I even understand how fstab works generally.  I spent several hours reading the man page and googling it. (I don't get some of the arcane options, but I do understand how it works generally.)

If I mount the HD at /home, and user directories are created underneath it, that essentially means I can only put user directories on the HD.  I want to have other things on the hard drive. Is the only way to do that to partition the hard drive into two partitions?

Sure you can.  With parted you can have up to 128 partitions I believe.  That would not be practical however.  How big is the drive over all?

Edit: You could mount the separate partitions anywhere in the file system.  One at /home and one at /srv/samba if you were going to do file sharing.

---

### Post by greatkingrat2 on 2013-11-09
> **bab1 said:**
> Sure you can.  With parted you can have up to 128 partitions I believe.  That would not be practical however.  How big is the drive over all?

Edit: You could mount the separate partitions anywhere in the file system.  One at /home and one at /srv/samba if you were going to do file sharing.

I would prefer to have only one partition.  I believe I stated that more than once.  Is there a way to put common folders and users home folders on one partition and mount that partition as /home?  If so, please tell me how.

---

### Post by bab1 on 2013-11-09
> **greatkingrat2 said:**
> I would prefer to have only one partition.  I believe I stated that more than once.  Is there a way to put common folders and users home folders on one partition and mount that partition as /home?  If so, please tell me how.

What you are asking isn't very clear.  If you mount the partition at /home, everything you create will be below that.  After all it is a hierarchical system.  You can create a directory with any name on it under /home.  Typically you only have a directory for each user and these are usually named the same as the users login.  Such as```

/
  home/
              bill
              george
              jill


```

What directories were you thinking of adding and where would you think they should be located?

---

### Post by greatkingrat2 on 2013-11-09
I want the hard drive to have this on one partition:

userfoldersroot/user1
userfoldersroot/user2
sharedroot/project1
sharedroot/project2

I would like to alias/mount userfoldersroot/ as  /home/ 
And alias/mount sharedroot as /data/

That's what I would like to do.

---

### Post by Impavidus on 2013-11-09
> **greatkingrat2 said:**
> It was mounted in /media when it came from system76.  What sequence of commands should I be running to do this properly that accomplishes the following:

1. puts the user folders on the secondary hard drive.
2. allows me to have the HD as one partition (**I don't like managing partitions**)
3. keeps the user folders on the HD separate from other folders

If I mount it in fstab as /home, I can't do 3 unless I don't get 2.  Unless I'm missing something.  I really don't care if the drive is mounted in /media.  That's just where it was mounted when I got the machine.
Many beginners don't like managing partitions, because they fear to lose data, but trying to accomplish what you want without managing partitions seems far more complicated. Creating a second partition on your HD is the easiest way out of your problem.

---

### Post by deadflowr on 2013-11-09
> **greatkingrat2 said:**
> I have no idea what you are talking about with respect to needing to input the full path.  I don't want to input a full path.

My bad.
I was reading something else, and got mixed up.

But I was wondering how you came to the conclusion that the dash started you in /home/user, or /media/whatever.

---

### Post by bab1 on 2013-11-09
> **greatkingrat2 said:**
> I want the hard drive to have this on one partition:

userfoldersroot/user1
userfoldersroot/user2
sharedroot/project1
sharedroot/project2

I would like to alias/mount userfoldersroot/ as  /home/ 
And alias/mount sharedroot as /data/

That's what I would like to do.

Not going to happen.  There are no aliases with directories (or files for that matter).  The human readable names are already linked to the inode which is really how you locate where the object is located in the file system.  The directory name is the link.  The sym-link points to the path to that name.  The hard link is a name that points to the same inode as the original name.

The proper way to do this is for you to decide what directory structure you want to use and what device/partitioning you want to employ to store that data.  As @Impavidus has said, you really should get used to how this works for everyone else using Linux.  if not you will have endless problems with applications that developers have expected the prevailing scheme and overly complicated file system methods.

Here is how I would handle your stated needs:

```

1st HDD = sda (the SSD device)
2nd HDD = sdb

1st partition on sda = [COLOR="#FF0000"]sda1[/COLOR] (this is the entire SSD)

1st partition on sdb = [COLOR="#0000FF"]** sdb1**[/COLOR] (this could be 30% of the HDD)
2nd partition on sdb = [COLOR="#006400"]**sdb2**[/COLOR] (this could be 70% of the HDD)

All partitions ([COLOR="#FF0000"]sda1[/COLOR], [COLOR="#0000FF"]**sdb1**[/COLOR], [COLOR="#006400"]**sdb2**[/COLOR]) are formated with EXT4 file system

The file system is mounted like this
[COLOR="#FF0000"]/ [/COLOR]= root file system = sda1 (includes everything except /home and /srv/projects)
[COLOR="#FF0000"]/[/COLOR][COLOR="#0000FF"]**home**[/COLOR] = sdb1 (the home directories)
[COLOR="#FF0000"]/srv[/COLOR][COLOR="#006400"]**/projects **[/COLOR] = sdb2 ( the projects are stored here)

```

Some of the benefits are: [LIST]
[*]a single sym-link in each users home directory is all that is needed to access the projects
[*]all the applications function correctly 
[*]the projects directory or any part thereof can be shared between computers
[*] multiple users can share a single project and still have their own private users directory
[*] you can backup all of the project files with a single simple command if you desired.
[/LIST]

You can alter the size of the partitions and you can alter the location of the /srv/project mount point (it could just as easily be /data/projects).  You should not alter the /home directory mount point with out more considered thought as to the ramifications.

---

### Post by ian-weisser on 2013-11-09
That's a great explanation, and a very simple result for the user. Use of color really makes it clear!

---

### Post by greatkingrat2 on 2013-11-09
So y'all are saying /home cannot be a symlink ?  It has to be either a physical directory or a mounted drive?

---

### Post by bab1 on 2013-11-09
> **greatkingrat2 said:**
> So y'all are saying /home cannot be a symlink ?  It has to be either a physical directory or a mounted drive?
The users *home directory* is  never a symlink in a Linux file system.  It can be mounted anywhere, but that is different than making a symlink.  The data inside is a different matter.  do you understand file system hierarchy and what a file system path represents?  

You really have 2 issues here; how to define the users home directory and where to store data that should NOT be in a users home directory.  it's a simple fix that you seem to be resisting.  Are there other considerations that we don't know about?

[COLOR="#0000FF"]Edit:  In a Linux file system the directory is always on a mounted drive, even if that drive is the only SSD or HDD in the system.  The way you are using the term "mounted drive" is a Windows thing.  Windows drives are partitions formatted with a file system.  Just like Linux they are mounted into the root file system.  The terms C: or D: are just labels for the various partitions. [/COLOR]

---

### Post by greatkingrat2 on 2013-11-09
This is what I wrote at the very beginning:
>  have two hard drives. An SSD mounted at / and a HD mounted at /media/HD1. I created a folder called home on the HD, copied /home to that folder, and then changed /home to be a symlink to /media/HD1/home. Almost everything works.
All you needed to do was say something like "/home cannot be a symlink. Here's some documentation: http://blah.com/". I have no idea what all the other blather is about.  I answered questions thinking maybe there'd be another way to do what I want. Why it took 3 pages to get to that...

> do you understand file system hierarchy and what a file system path represents? 
This is me rolling my eyes.   I'm new to Linux, but I'm not dumb.

---

### Post by bab1 on 2013-11-09
> **greatkingrat2 said:**
> This is what I wrote at the very beginning:

All you needed to do was say something like "/home cannot be a symlink. Here's some documentation: http://blah.com/". I have no idea what all the other blather is about.  I answered questions thinking maybe there'd be another way to do what I want. Why it took 3 pages to get to that...


This is me rolling my eyes.   I'm new to Linux, but I'm not dumb.

But you do have a problem communicating.  ;-)

---

