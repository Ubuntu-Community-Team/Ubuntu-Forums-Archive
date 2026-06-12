---
title: "Google Chrome- download error - Failed Insufficient permissions"
date: 2017-11-16
forum: New to Ubuntu
---

### Post by comicguy on 2017-11-16
Hey Guys,

I am a total newbie and not really into coding and stuff. 
Now the error that i am getting is whenever i try to download a file to a particular folder from chrome it says 'Failed - Insufficient Permissions' but the same file can be downloaded to my 'Home' folder which is a default directory for downloads .
 I am stuck and have googled everything but couldn't find any solution.
Hope you guys can help. 

Thanks

---

### Post by Holger_Gehrke on 2017-11-16
On Linux there is system of permissions which is strictly enforced to protect the system from user error or malevolent users or programs. Every file or directory has an owner and a group and there are permissions for the owner, the group and all others to read, write or execute a file or use a directory as your working directory. As a normal user you don't have the right to write anywhere except your home directory and it's subdirectories, /tmp (the directory for temporary files) and the subdirectories of /media/"yourUsername" into which media you've connected to the computer are mounted.
If you know how, you can put files anywhere, but usually by the time you know, you'll understand what the various directories are meant for and won't want to put things there.

Holger

---

### Post by ajgreeny on 2017-11-16
Where are you trying to save these downloads?

Holger is correct with his comments about permissions, and from what you have said it sounds as if you're trying to save things to a folder in the OS's file system, not into the Downloads folder in your home which is usually where browsers send downloads.

---

### Post by vasa1 on 2017-11-16
> **comicguy said:**
> Hey Guys,

I am a total newbie and not really into coding and stuff. 
Now the error that i am getting is whenever i try to download a file to a particular folder from chrome it says 'Failed - Insufficient Permissions' but the same file can be downloaded to my 'Home' folder which is a default directory for downloads .
 I am stuck and have googled everything but couldn't find any solution.
Hope you guys can help. 

ThanksYes, people would help you if you specify what you mean by "a particular folder". Where is this, what is its name, what its path? I'm confident you can provide that information.

---

### Post by photonxp on 2017-11-18
Change the Downloads folder of chrome browser to another folder where you have the permissions might help:
**[How to Change the Chrome Download Folder Location]("https://www.howtogeek.com/231002/how-to-change-the-chrome-download-folder-location/")**


If that doesn't help, copy your "Download location" of chrome here if that's possible.

---

### Post by jrussell88 on 2018-10-29
I am having the same problem. 

Chromium Version 70.0.3538.77 (Official Build) snap (64-bit), fresh install of Ubuntu 18.10 desktop.

I can download files to my /home folder, but not to other folders on separate partitions where I have ownership and r/w access. These partitions are on USB drives; previously using the repo version of Chromium on Ubuntu 17.04 this wasn't an issue. 

I can create, read and write files to these partitions from the command line, folder permissions are  rwx for everyone on an NTFS folder,; the same issue arises with ext4 folders which are r/w for my group and I'm the owner. 

Does Chromium have a distinct Group? Or need to be added to a Group?

---

### Post by slickymaster on 2018-10-29
Old thread closed

@jrussell88: Please start a new thread in the General Help or New to Ubuntu sub-forums

---

