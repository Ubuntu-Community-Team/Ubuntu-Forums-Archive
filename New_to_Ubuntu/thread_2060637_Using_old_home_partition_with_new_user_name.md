---
title: "Using old home partition with new user name"
date: 2012-09-20
forum: New to Ubuntu
---

### Post by lirantha on 2012-09-20
So, I tried to work with my old hard drive partitions manually during an  installation of 12.04, but ended up not correctly assigning the old 500  GB partition I'd created as my  /home folder.  Couldn't figure out why I  was getting an error message, so I just picked the first option from  the installation program and hoped it would overwrite my old versions of  Ubuntu without changing the partitioning of the drive.

So far,  so good!  I then managed to relocate this tutorial about changing the  home partition:  [http://help.ubuntu.com/community/Partitioning/Home/Moving](http://help.ubuntu.com/community/Partitioning/Home/Moving)

There's  nothing in the current home folder that I want to keep, so I figured I  could leave out all of the copying. The partition I want to use is at  /dev/sda5, ext4 format.

So my question is, if I copy this into fstab:

```
# (identifier)  (location, eg sda5)   (format, eg ext3 or ext4)      (some settings)
UUID=???????????   /home    ext4          nodev,nosuid       0       2
```...with the correct UUID and so forth, will that do the trick?

The  other complication is this: I had two different users set up with my  previous install, and each has a  folder in the old 500 GB partition.  I want to keep the old root  or primary user folder (e.g., "PrimaryUser").  But when I did the clean  install, I accidentally changed the  primary user name from "PrimaryUser" to (say) "User1".  Will I need to  change the name of the "PrimaryUser" folder to "User1" in order for  everything to work properly?  Or change my current user name so it matches the old one?  And if so, how would I go about doing that?

Thanks in advance for that help.  :)

---

### Post by ajgreeny on 2012-09-20
A separate /home partition is identified and mounted in fstab by the entry
```
UUID=e2554df2-7e16-4864-97c9-834d8bebecda /home           ext4    defaults        0       2
``` on my system, so editing your fstab to contain a line similar to that but with your own UUID which you can get from command **sudo blkid**, or in recovery mode just **blkid**.

However, even when mounted by fstab, the files and folders in that /home partition will still be owned by the wrongly named owner, I think, so you will still need to change the ownership of those with ```
sudo chown -R *newuser:newuser* /home/*newuser*
```  You may need to do all of those changes in recovery mode as I am not sure what will happen to the new /home made by the system when the old one did not work as you expected.

---

### Post by lirantha on 2012-09-20
Did the first part of the above while logged in normally.  Then tried to restart. Couldn't log in.  Typed the password, hit enter, and it just asked for the password again.

Booted into safe mode where it has all the menus and tried the ```
sudo chown -R *newuser:newuser* /home/*newuser*
```
thing from the 'drop to root' option, 'cause I had no idea where else to enter it.  It told me that /home/*newuser* didn't exist.  So I repeated the code but just did /home.  That seemed to be an acceptable command.  Then I couldn't figure out how to start Ubuntu normally from where I was, so I shut off the computer and restarted. Same log-in problem.

Currently logged in as a guest.

---

### Post by lirantha on 2012-09-20
Okay, so, under the assumption that I had done something dramatic and potentially irreversible to my system given the last post, I went ahead and tried a fresh install.

This time, figured out how to use my pre-existing partitions, with dev/sda1 mounted as /, and dev/sda5 mounted as /home, the way they used to be.  System booted, home folder was correctly mounted, all files from /home folder intact - hurrah!

...but now my wireless card isn't working.  At all.  No networks listed.  So I'm off to try to fix that.  Thanks for the help, ajgreeny.

**EDIT:** Fixed wireless issue by reinstalling OS - for the third time today - and connecting to the Internet during installation.  Knew it wasn't a hardware/driver issue 'cause wireless worked when I booted from CD.  Don't know why it decided my wireless card shouldn't work unless I had used it during install, but at least it's fixed for now.  Here's hoping it stays that way.  :P

---

### Post by JKyleOKC on 2012-09-20
You did the right thing by re-installing. Your home directory is always a subdirectory of /home so your "chown -R" changed the permissions of the subdirectories -- but the system requires that /home itself be owned by root and be writable only by the super user.

I have no idea why the wireless card didn't work until the second re-install, but it might have needed some third-party package that had to be downloaded during the install process. Anyway now that all is working, it should continue to do so.

---

