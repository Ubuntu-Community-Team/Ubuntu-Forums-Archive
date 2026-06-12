---
title: "Best practice for backing up and restoring Glusterfs 3.4 Share"
date: 2015-01-23
forum: New to Ubuntu
---

### Post by craig37 on 2015-01-23
Hi,

Very new to Ubuntu so hoping to find some help and guidance with a task that I have.

We have a Glusterfs share (3.4) that contains hundreds of thousands of files within numerous sub folders. I need to be able to take a backup of the share exactly how it is (file paths and permissions included if possible) and then be able to restore the whole share exactly how it is now.

I have successfully created a tar of the share which seems to have backed up all files and subfolders including permissions, however when I extract the tar file the share does not restore to the state it is in now.

The current file structure for the share is: /mnt/glustershare/folderA/folderB/etc/etc

The tar backs this up fine but when I restore the tar file to the glustershare path it creates: /mnt/glustershare/mnt/glustershare/folderA/folderB/etc/etc

I am pretty sure it is something simple that I am doing wrong when it comes to extracting the file, however i have tried extracting the file to root which just puts it in root and if I extract at /mnt instead of /mnt/glustershare then i still get /mnt/mnt/glustershare

The only thing i can think to do, is to delete the whole share then restore but surely there is a simpler way than that? 

Any help much appreciated!

---

### Post by TheFu on 2015-01-23
Tar is really old-school.  For backing up a few MB, it is fine, but if there are GB involved, it is not very efficient. There are better solutions.

Is the issue you have just the location where the restore gets placed? It isn't clear.
If so, be certain that you understand relative paths and what the cwd is when dealing with tar - both on backup and on restore.  I avoid absolute paths in tar files. Makes restoring more flexible.

The subject asked for best backup practices: 

    Stable / Works Every Time
    Automatic
    Different Storage Media
    Fast
    Efficient
    Secure
    Versioned
    Offsite / Remote
    Restore Tested

---

### Post by Holger_Gehrke on 2015-01-23
Use the option '--strip-components n' during extraction, this removes n levels of directories from the beginning of filenames during restoration.

---

### Post by craig37 on 2015-01-28
Thank you both for your replies. Really sorry for the delay in getting back to you but I didn't recieve notification that my post had been replied to and I have been out the office the last couple of days.

TheFu: Yes this would be for a file share for multiple servers so it will contain hundreds of GB in size. Yes the issue at present that i am finding is when I tar the files currently, it not only backs up the files but also the file share path. So when I delete all the files and try restoring all files, they do restore however they restore with the file share name at the beginning so it creates extra folders if that makes sense? So where we currently have /mnt/glustershare/then all our files and folders     after i delete and extract the tar on the share I get the files back however the share is then listed as /mnt/glustershare/mnt/glustershare/all our files and folders

I am very new to Ubuntu so as you suggested this may not be the best way of backing up and restoring so many files. Is there a particular solution you would recommend instead?


Holger_Gehrke:  Thanks for the suggestion, I will try this now and let you know how I get on.

Thanks

---

### Post by craig37 on 2015-01-28
I am probably missing something really silly but I cannot get the option '--strip-components n' to work. I have been entering the following command:

sudo tar -xvf /home/sturc/GlustershareBackup.tar.gz -C /mnt/glustershare/ --strip-components n

I get a message saying invalid number of elements.

---

### Post by Holger_Gehrke on 2015-01-28
> **craig37 said:**
> I am probably missing something really silly but I cannot get the option '--strip-components n' to work. I have been entering the following command:

sudo tar -xvf /home/sturc/GlustershareBackup.tar.gz -C /mnt/glustershare/ --strip-components n

I get a message saying invalid number of elements.

Replace the 'n' with the number of components you want to get rid of. Example: '--strip-components 1' would remove 'mnt/', '--strip-components 2' would remove 'mnt/glustershare/' and so on ...

---

### Post by craig37 on 2015-01-28
Aah right sorry I see what you mean now. Excellent, I have just tested that in my test environment and that has restored the files as I wanted without the additional /mnt/glustershare folders.

Thanks for you help with that

---

### Post by TheFu on 2015-01-28
> **craig37 said:**
> Thank you both for your replies. Really sorry for the delay in getting back to you but I didn't recieve notification that my post had been replied to and I have been out the office the last couple of days.

TheFu: Yes this would be for a file share for multiple servers so it will contain hundreds of GB in size. Yes the issue at present that i am finding is when I tar the files currently, it not only backs up the files but also the file share path. So when I delete all the files and try restoring all files, they do restore however they restore with the file share name at the beginning so it creates extra folders if that makes sense? So where we currently have /mnt/glustershare/then all our files and folders     after i delete and extract the tar on the share I get the files back however the share is then listed as /mnt/glustershare/mnt/glustershare/all our files and folders

I am very new to Ubuntu so as you suggested this may not be the best way of backing up and restoring so many files. Is there a particular solution you would recommend instead?


Holger_Gehrke:  Thanks for the suggestion, I will try this now and let you know how I get on.

Thanks

Set the email notification for replies to your account here.

Any non-tar-like backup tool will work better.  I like **rdiff-backup**. duplicity is another and backups using rsync with versioning is also popular. There are lots and lots of posts here and elsewhere about each tool.  From my list of best practices above, duplicity is the best fit. I don't like the way it stores the files in chunks which makes restoring a single file from yesterday a little harder than it needs to be.  rdiff-backup does versioning, but the most recent backup looks like a mirror. Further, it captures any ownership/group/permissions changes at metadata, unlike the rsync solution which only retains the most recent permissions.  The commands for rsync and rdiff-backup are very similar, so why not use the tool that does more, easier?

Seems you are very new.  A little directed reading now will reduce your frustration greatly. [http://blog.jdpfu.com/2014/12/28/learning-linux](http://blog.jdpfu.com/2014/12/28/learning-linux) has links in order from basic knowledge to the cusp of intermediate use.  Gaining a little background today with the most critical ideas in UNIX will help you shift your mind to the UNIX-way of thinking where the entire OS is a development tool for all users.

---

### Post by craig37 on 2015-01-28
Thanks for that. Really appreciate your feedback and advice.

Thank link will be very helpful because a syou said I am very new to Linux so will help me gain a better understanding. I think in our environment, the rdiff-backup tool may be the most sutiable tool as we will have to restore individual files mainly and permissions is also another key factor.

Thanks again for the help and guidance.

---

