---
title: "USB Hard drive locked?"
date: 2014-09-10
forum: New to Ubuntu
---

### Post by rod52 on 2014-09-10
I originally installed Lubuntu and used gparted to format the external drive.  Then decided to install Ubuntu.  Now I cannot create folders etc.  Gparted says I am not the owner.  Did installing Ubuntu change permissions?  If so, how do I change them so I can create folders read and write to it.

---

### Post by yancek on 2014-09-10
Where did you install Ubuntu, the internal or external drive?  Do you still have Lubuntu as well as Ubuntu?  If you have both systems installed then the expected behavior is that from Lubuntu, you would not be able to write to the partition which has Ubuntu unless you were logged in or tried to write as the root user, using sudo .  The reverse is also true and you would have to change permissions but first, explain what you have.

---

### Post by rod52 on 2014-09-12
Lubuntu was installed on the internal HD.  That is when I formatted the external Hd.  I then switched to Ubuntu (fresh install).  So Lununtu is on longer installed.  I intend to use the external for backups.  The external was never connected during either installation.  It was connected and formatted to EXT4 after I had installed Lunbutu.  But as I said. Lubuntu is no longer installed.  Gparted was never used to partition either HD.  I only used it to format the external HD.

---

### Post by grahammechanical on 2014-09-12
Have you created folders on this external hard disk? Have your stored files on this external hard disk? What does the File Manager report about this partition? I do not understand what Gparted has to do with this. Do you want to create more partitions on this external hard disk? Then run Gparted from a Ubuntu live session. If you are running Gparted from an installed session it might need to be run with administrator privileges.

I have used Gparted from a live session many times to create/delete and resize/move partitions. I have never been refused because I was not the owner. If you have created folders then you might need to run File Manager with administrator privileges and use it to change the access permissions of the folders and the files in the folders. Change the permission for Groups and Others from Access files to Create and Delete files.

Regards.

---

### Post by rod52 on 2014-09-12
There are no folders files, nothing.  This is what happened. I migrated from XP to Lubuntu.  So that external HD was used with that OS. After I installed Lubuntu, I used gparted only to reformat that external HD to insure Lubuntu could read and write to it.  I have not used it yet.  I discovered the problem after changing to Ubuntu and performing a backup.  I was going to copy the backup to that external HD.  But I could not.  So I opened gparted thinking maybe I had to reformat again and just to see what file system was installed.  All looked good, but gparted aid I was not the owner.  But I am, I have admin privileges.

---

### Post by redrumrogue on 2014-09-15
When you installed Ubuntu did you create a user with the same username you had in lubuntu?  If the username or user ID is different then it may be that you have an issue with filesystem ownership.  You could try and change the owner of the device to your new ubuntu user with this ...
**sudo chown -R (user name) /dev/(device name)******

---

### Post by rod52 on 2014-09-17
Thanks redrumrogue,  I no longer see that I am not the owner.  But I still cannot copy a folder and paste to that drive.  Paste is faded.  Trying to copy the folder I believe is the backup folder. Trying to this from the file manager.  And yes, I had changed the user name.  Still learning that I have to be careful when re-installing the OS, that I do not changer the user name etc.

---

### Post by rod52 on 2014-09-17
Nope, I was wrong.  Checking permissions with gparted still says I am not the owner.  When using chown. Do I have to do it from within the external HD directory?  Or is there another way to change permissions?

---

### Post by rod52 on 2014-09-17
Upon further investigation, I did not notice that gparted says the external HD owner is root, and group is root, if that helps.

---

### Post by rod52 on 2014-09-17
I really need to pat attention so I am not wasting peoples time.  Its not gparted reporting that I am not the owner, its the file manager.  When the external drive is hi-lited and I right click in the empty space where you would see any files. I click property and permissions.  Thats where it says I am not the owner.  It says that the root is both owner and group.  When I formated the external HD, I just formated to EXT4.  Don't know if I needed to do something else.  I did try sudo chown -R "name" /dev/"device name" as suggested.  When I go to media, I do see the name of the owner name as a folder on the drive. So it looks like the command worked, but don't understand why the file manager reports differently, Unless that is just a Linux thing.

---

### Post by sotiris2 on 2014-09-19
I dont think chown can work on /dev/devicename nor that it would be good a file on /dev to not be owned by root. 
You will have to use the command on the folder the external drive is being mounted. To find where it is being mounted, mount it as normally (via gui?) and use the terminal command ```
mount
``` Note where it is being mounted for example lets say */media/rod52/RANDOMSTUFF* and with it still mounted do ```
sudo chown -R rod52:rod52 /media/rod52/RANDOMSTUFF
``` if your username is rod52, otherwise replace rod52 with your actual username.

---

### Post by JKyleOKC on 2014-09-19
> **sotiris2 said:**
> I dont think chown can work on /dev/devicename nor that it would be good a file on /dev to not be owned by root. 
**You will have to use the command on the folder the external drive is being mounted. **To find where it is being mounted, mount it as normally (via gui?) and use the terminal command ```
mount
``` Note where it is being mounted for example lets say */media/rod52/RANDOMSTUFF* and with it still mounted do ```
sudo chown -R rod52:rod52 /media/rod52/RANDOMSTUFF
``` if your username is rod52, otherwise replace rod52 with your actual username.Even that won't work; the mount command assigns ownership to root by default and chown cannot override this.

In the thread at [http://ubuntuforums.org/showthread.php?t=2244221&p=13122116#post13122116](http://ubuntuforums.org/showthread.php?t=2244221&p=13122116#post13122116) I spelled out for another person how to cure the problem. This might be a good candidate for a sticky since the question shows up almost as often as the "black screen at boot" situation which is easily the most common problem of all...

---

