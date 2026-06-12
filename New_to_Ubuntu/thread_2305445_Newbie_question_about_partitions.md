---
title: "Newbie question about partitions"
date: 2015-12-06
forum: New to Ubuntu
---

### Post by at35z on 2015-12-06
Hi there,

This was the first time I installed Linux entirely from an Ubuntu disc and wanted to create 2 partitions (on previous installs of mine the PC either had them already separated or I did not make any changes), one for the system and another one for the important files that I would like to keep, even when I reinstall the system with clearing everything on the partition.

I did kind of mess things up. :redface: I created one for the system which works as I wanted it to do, and the other one seems to be invisible. I'm pretty sure I was the one who set things up incorrectly for such intention.

Here is a screenshot of GParted, showing my partitions:

[img]http://i.imgur.com/Z1IutDK.png[/img]

When I install a game on Steam, it asks which partition I'd like to use, however, I can't access the partition with the File manager simply to put some files on it, which I would like to.

So basically I just want that other partition to be available in the file manager so I can access it and put some of my important files on it. How could I make this work?

Thanks in advance! :)

---

### Post by Skaperen on 2015-12-06
the partition is there, but it is not mounted.  did you create it during the installation of Ubuntu? i guess not.

normally the installation will set it up by formatting it and configuring it to be mounted.  now you have 2 options. you can format it and edit files to make it be mounted at boot ***-or-*** you can do the install again and select /dev/sda5 during the volume setup stage.

---

### Post by at35z on 2015-12-06
> **Skaperen said:**
> the partition is there, but it is not mounted.  did you create it during the installation of Ubuntu? i guess not.

normally the installation will set it up by formatting it and configuring it to be mounted.  now you have 2 options. you can format it and edit files to make it be mounted at boot ***-or-*** you can do the install again and select /dev/sda5 during the volume setup stage.

I actually **did** create it during the installation, and it says it's technically mounted (Edit: I can only Unmount it):

[IMG]http://i.imgur.com/mWLyNbQ.png[/IMG]

---

### Post by SlidingHorn on 2015-12-06
I could very well be wrong, but I'm thinking it could be your mount point?   Is there a reason you have it set to /usr/local?  Not something I've seen often in my minimal experience.

---

### Post by at35z on 2015-12-06
> **SlidingHorn said:**
> I could very well be wrong, but I'm thinking it could be your mount point?   Is there a reason you have it set to /usr/local?  Not something I've seen often in my minimal experience.

When I created it, it did not let me choose "/" as the mount point because it's already in use, so I had to pick another one and as a newbie I could not really see the difference between the choices. I guess it was the wrong one. Any way to change it now?

---

### Post by SlidingHorn on 2015-12-06
The /usr... path isn't writable by normal users, as it's owned by root.  This would probably cause a lot of issues.  

A more likely mount point would be /home.  A lot of people like to create a /home partition so that their personal configuration files, photos are separate from the system files.

In your case, you could have / (for your system files)  and /home  (for your users' personal files).  Again, I could be wrong, but you'll likely have to do a new install once the partitions are fixed.  

The naming structure may be a little confusing, but directories like /var, /lib, /usr, /etc, etc. ;) are all system directories.  By default, when you create your first user, its "home" directory will be /home/<user>.  In there, you'll already have directories for "Downloads," "Documents," "Music," etc.  That's (/home) where USERS will store their personal iems, so that's where you should mount your partition. :)

---

### Post by buzzingrobot on 2015-12-06
The '/' partition is mandatory.  (The only mandatory partition, actually).  

GParted shows /usr/local as the mount point for sda5. Your inability to access /usr/local with the file manager is probably because you, as an ordinary user, lack permission to alter the contents of the /usr/local directory. (/usr/local is owned by root.)

You've allocated slightly less than half the disk space to /usr/local.  That's an unusually large amount for the partition.

If your goal is to keep important files on a partition that can remain unaltered during a reinstall, your /home directory is the appropriate place for that. You have full rights to do as you please there.  You might consider repartitioning to mount your home folder on its own partition. There no need to create a specific partition on which to mount /usr/local, since *all* directories are subordinate to the '/' directory and will be created on the partition where it is mounted if not specifically given their own partition.

When you do a reinstall, to preserve the contents of your /home folder, choose the "Something Else..." option in the installer's partitioning section and then be sure to indicate that the existing home partition should be mounted on /home but *do not* check the formatting box. The new system will mount that partition on /home but will not format it, leaving its content intact.

---

### Post by bab1 on 2015-12-06
> **at35z said:**
> ... Any way to change it now?
Not easily.  Everything that is at /usr/local is on the separate partition.  This is the data I am referring to```
ls -l /usr/local
total 32K
drwxr-xr-x 2 root root 4.0K Dec  4 15:57 bin
drwxr-xr-x 2 root root 4.0K Apr 16  2014 etc
drwxr-xr-x 2 root root 4.0K Apr 16  2014 games
drwxr-xr-x 2 root root 4.0K Apr 16  2014 include
drwxr-xr-x 4 root root 4.0K Apr 16  2014 lib
lrwxrwxrwx 1 root root    9 Jan  3  2015 man -> share/man
drwxr-xr-x 2 root root 4.0K Apr 16  2014 sbin
drwxr-xr-x 7 root root 4.0K Apr 16  2014 share
drwxr-xr-x 2 root root 4.0K Apr 16  2014 src

```
All of the above will  have to be temporarily moved to a location the is on /*dev//sda1*  Something like* /usr/temp* will work.  You will also need to do the same for /home.  Maybe **/temp/home**.  Then you can unmount the partition (/dev/sda5) and remount it at /home.  Then you make the change persistent by modifying the fstab file line in question by changiing the **usr/local **entry to **/home**.

As you can see this is pretty extensive and you need to use sudo to act as the root user.  My advice is to save your personal files on a flash drive and reinstall.  It will be quicker and a lot less painful.

---

### Post by at35z on 2015-12-06
Thanks everyone, you were really informative, I will fix this during another installation.

---

