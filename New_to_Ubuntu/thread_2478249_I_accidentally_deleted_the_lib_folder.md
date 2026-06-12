---
title: "I accidentally deleted the lib folder"
date: 2022-08-21
forum: New to Ubuntu
---

### Post by ayudaayuda37 on 2022-08-21
I'm sorry if I'm not well understood, I don't speak English and I'm using a translator to write the message. I add that I am new to Ubuntu.
I had a problem when running an application, it told me that it could not find a file in a path. So I followed the path and created a /lib folder in that path to try to fix the problem. I tried to run the app again and the problem was not resolved. So I tried to revert the changes I made which was to create that /lib folder and a file inside the folder. To remove the folder I used sudo rm -r /lib. Or at least I think that was the command I used. After a few seconds my terminal closed and I couldn't launch it again. A few minutes passed, my pc went to sleep and when I tried to access again it did not recognize the space where I entered my user password. Therefore I turned it off, now that I turn it on it shows me the following, in addition to other error lines:
run-init: can't execute '/sbin/init' No such file or directory


I think I made a mistake in the path and did not delete the /lib folder from the directory I was in, instead I deleted some lib folder from the root of my system. I would like to know if I can revert the changes to recover the system.


UPDATE: I tried to repair my OS, I booted Ubuntu in test mode from a USB. I went to the root and compared the folders that exist on my damaged pc vs. the folders that exist on my startup in test mode. Sure enough, there is no lib folder.
How could I get her back? I tried to copy with "sudo cp -r /lib /dev/[name that is assigned to the partition with my damaged OS]". The command runs but the /lib folder is not pasted.

---

### Post by TheFu on 2022-08-21
If there are files on the system that you don't want to lose, use a flash-drive with Ubuntu in the "Try Ubuntu" mode and backup all those files first.

/lib is a critical directory.  Reinstall or restore from backups. Those are the only options.

You aren't the first to do this sort of thing, but it was a really, really, bad thing to do.  Be careful using sudo when you aren't 100% certain what a command actually does.


Live and learn.

---

### Post by Impavidus on 2022-08-21
> **ayudaayuda37 said:**
> To remove the folder I used sudo rm -r /lib. Or at least I think that was the command I used. After a few seconds my terminal closed and I couldn't launch it again.What happened here depends on a bit on the details of your Ubuntu system. It's different for Ubuntu 22.04 compared to Ubuntu 20.04. In any case, this command uses the path /lib (mind the leading /), which is an absolute path, so it removes the /lib in the root directory and all its contents. On Ubuntu 20.04, this is really bad, as /lib contains some files that are vital to running nearly all applications. It makes running anything pretty much impossible. On Ubuntu 22.04 however, /lib is normally a symbolic link to /usr/lib and that command would only delete that symbolic link, which shouldn't have any consequences. I suspect you don't use Ubuntu 22.04.

> I would like to know if I can revert the changes to recover the system.There's no revert for deletion of files and directories.

> I tried to copy with "sudo cp -r /lib /dev/[name that is assigned to the partition with my damaged OS]". The command runs but the /lib folder is not pasted.
The contents of /lib on a live disk are different from those on the installed system, so even if this copy worked, it wouldn't have fixed the problem. However, copying something to /dev/[name that is assigned to the partition with my damaged OS] doesn't have the effect you expected. /dev/some_block_device contains the raw sequence of zeros and ones on your harddrive. Whenever you copy something there that isn't a disk image, the result is garbage. You may have created garbage on /dev/[name that is assigned to the partition with my damaged OS].

Some technical stuff:
If the /lib on the live disk you copied from is an actual directory, this command should have given you an error message, as you cannot copy a directory to something that's not a directory. If the /lib on your live disk is a symbolic link, it would have written the symbolic link to the block device, which might be bad news. However, I don't know the details of the /dev pseudofilesystem. Normally, symlinks are stored entirely in the inode table entry for the link, not in the data blocks themselves, so this might not have overwritten the partition.

If you didn't create garbage on the partition of your damaged OS, you can rescue files from there, if you didn't have backups. If you did create garbage, rescuing files becomes much harder and I really hope you've got backups in that case. Then you could reinstall every package that has something in /lib using the live disk, but this is a very complex operation. It's better to just reinstall Ubuntu.

---

### Post by ayudaayuda37 on 2022-08-21
I would have liked to repair the system because I have system settings that I want to keep. But the two answers I received agree that I should reinstall the system. Thank you very much for the reply.

---

### Post by ayudaayuda37 on 2022-08-21
The version of Ubuntu that I have installed is 22.04.
I would have liked to repair the system because I have system settings that I want to keep. But the two answers I received agree that I should reinstall the system. Thank you very much for the reply.

---

### Post by TheFu on 2022-08-21
> **ayudaayuda37 said:**
> I would have liked to repair the system because I have system settings that I want to keep. But the two answers I received agree that I should reinstall the system. Thank you very much for the reply.

If you want to repair a system in the future, be certain to make sufficient backups in the past.  There's no magic with any OS if you did the same thing.

---

### Post by Impavidus on 2022-08-22
You may still be able to keep your home directory, where most of your settings are. Just create a backup (if you haven't already) and restore it after the reinstall. Or install Ubuntu over the old system without formatting. Or, if you use a separate /home partition, just reuse that /home partition without formatting it.

---

