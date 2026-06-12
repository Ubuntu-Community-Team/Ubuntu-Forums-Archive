---
title: "Deleting a /home/john folder"
date: 2012-07-27
forum: New to Ubuntu
---

### Post by jhurley14 on 2012-07-27
Hola ubuntu users. Got a new external hdd. I went to what I assume is a sub folder of home, 'john', and copied and pasted it to my new hdd (this includes documents, downloads, etc). I now want to know:

1. how to delete the /john from the internal hard drive, since it only seems to include files (already moved to the external hdd)

2. how to make sure all future downloaded applications are installed on the internal hdd where ubuntu is installed

---

### Post by oldfred on 2012-07-27
Welcome to the forums.

The /home has a lot of hidden user settings for both system & applications. Do you want to move the entire /home to the external. That may break system as /home has to always be mounted where an external drive does not. Also what format is external. /home has to have a Linux format for permissions and ownership. Often externals are NTFS which is ok for data but not system settings.

To move /home uses rsync  
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

The actual user settings are small. My /home is 1GB with about 3/4 of that as .wine with Picasa which I have not yet moved to my /data. Because /home is small I now keep it as part of / (root).
Then I can have a fully functioning system on one drive but have data linked in from other partitions on other drives.

I have several installs of Ubuntu and want to share my data in all of them. I started sharing with a NTFS partition and XP. I still have my Firefox & Thunderbird profiles in a NTFS partition even though I do not boot XP. All new data goes into a ext3 partition.
Data can be shared without the possible conflicts of user settings being different in different versions. I only copy some settings from one install to the next, normally. But I have to separately back up /home and the /data partition. Also saves the error of reformating a /home partition accidentally. I never reformat my /data and just configure / for install.

Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata]("http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata")

---

### Post by jhurley14 on 2012-07-28
Hola ubuntu users. I copied a folder that contained my documents, downloads, pics, etc, to an external hdd. The question is, how do I delete the /john folder stored on the internal hdd (in the right window)?

---

### Post by ub07 on 2012-07-28
Before you delete any directories, you should got into settings ---> User Accounts and delete the user "john"  (highlight and use "-") and then it should be safe to remove the directory if the system doesn't do so automatically.

---

### Post by drmrgd on 2012-07-28
So are you saying that you don't want your home directory to be on your internal HDD anymore, but would rather it on the external drive?  If that's the case, it's a bit more complex than just simply deleting the local /home folder as your /home folder contains user specific settings that are important.  

The better way to do it is to change the mount point of /home to the external hard drive so that the system now knows where to look.  Here is some Community Documentation that describes the process in detail:

[https://help.ubuntu.com/community/MoveMountpointHowto/](https://help.ubuntu.com/community/MoveMountpointHowto/)

---

### Post by oldfred on 2012-07-28
Please do not post two threads with the same question. Threads merged.

---

### Post by ub07 on 2012-07-28
I am confused as to what you are asking. Do you want to delete the folder "john" or do you want to move your home folder over to an external hd or both?

---

### Post by Wirephire on 2012-07-28
oldfred has explained it very well. Since your home folder contains a lot of hidden files and folders with configs, you **shouldn't delete** it unless you're gonna create new user and use him. Read his post very carefully before doing any future step.


*~wph*

---

