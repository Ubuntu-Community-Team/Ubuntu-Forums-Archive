---
title: "[SOLVED] Can't tar to USB"
date: 2008-07-26
forum: New to Ubuntu
---

### Post by MooseMagnet on 2008-07-26
Here is the command results

rich@rich-laptop:~$ tar cvf /media/my_external/purple.tar  /home/rich/Test.odt
tar: Removing leading `/' from member names
/home/rich/Test.odt
rich@rich-laptop:~$ 

But it is not on the USB. I go to Places > Search for files > File System
and it does show it in /media/my_external

But it is not on the USB. 

Any ideas what I'm doing wrong. I can copy-paste or drag-drop files to the USB, but no results when I tar or rsync.

Thanks.

---

### Post by mattismyname on 2008-07-26
When you say it's not on the device do you mean you actually did an 'ls' on /media/my_external and the file did not show up?

Is there anything else on the device?  (Maybe it is full)

---

### Post by cariboo on 2008-07-26
Sometimes linux delays writing a file to a drive, if you ummount the usb drive it will probably give you a message to wait while it writes the file to the drive.

Jim

---

### Post by mattismyname on 2008-07-26
You can also run 'sync' to flush the filesystem buffers.

---

### Post by MooseMagnet on 2008-07-27
I've got it all fouled up.
Here's the result from ls:

rich@rich-laptop:~$ ls /media/my_external
Backup  purple.tar  Test.odt
rich@rich-laptop:~$ 

ls says it is there.

But when I double-click the USB drive icon (my_external) it has only one folder in it. That is lost+found. 

And when I look in Places > Home Folder > File System > media
it has 4 items:
cdrom
cdrom0
my_external
my_external_

I don't know where the extra 'my_external_' came from. 

my_external_ has only one item, lost+found
and 
my_external contains the tar files

Don't know what I did, and don't know how to fix it. I can surely use your help.

---

### Post by mattismyname on 2008-07-27
I'd probably unmount it all and start from the beginning.  Seems like somehow the thing got mounted twice.  You could even reboot to get it back to a clean state.

---

### Post by MooseMagnet on 2008-07-27
I think it's working ok now. I have been able to add an archive to the USB drive with the tar command, and a file with the rsync command.

I renamed the drive "USB". Then wrote the archive and file on it with the tar and rsync commands. Then went to nautilus and deleted the old folder "my_external". The new folder "USB" does NOT have the lost+found folder in it. Should it?

Another possible cause of the problem is that I created a new folder "Backup" on the drive by right-click > Create Folder in the USB file browser window. Maybe I should create new folders on the USB in some other way?

Thank you, all of you, for your help.

---

### Post by MooseMagnet on 2008-07-27
I made several mistakes. One is that I did a right-click > Create Folder within the USB drive browser window. And I did some copy-paste and drag-drop to the USB. Then messing around more, I seem to have mounted it twice, which caused the duplicate folders:

my_external
my_external_

Looks like I need to add everything to the USB via tar, rsync, or such - to maintain permissions, etc. NO copy-paste, and NO right-click > Create Folder from the USB browser window.

I used nautilus to delete everything. Then WAS able to write files on the drive with tar, and also with rsync.

But deleting everything like that also removed the lost+found folder. So, I did a fresh reformat to ext3 for a clean start.

* I'd like to do more testing, by adding archives, folders, files to the USB drive, can I "correctly" delete them by right-click > Move to Trash from within the USB drive browser window? Or do I need to use tar or rsync to remove them?

Thank you for helping!

---

### Post by mattismyname on 2008-07-27
there's no fundamental reason why you couldn't use nautilus to do all of those things. If nautilus doesn't work it would be considered a bug

---

