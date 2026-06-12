---
title: "error while getting the sharing information"
date: 2014-07-27
forum: New to Ubuntu
---

### Post by Gnusboy on 2014-07-27
Hello

I am trying to understand why there are locked files named "DishArc" and another file named "Lost+Found" on a Samsung external HD I want to use for backups. Neither of these files will open or allow any change in permissions. First here is an error message saying that I am not the owner and can't open them. I changed the permissions for all of the other files to allow full permissions, but then I get this error message:
**"There was an error while getting the sharing information" **followed by "[B]'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory Please ask your system administrator to enable user sharing."
[/B]
Now I have three windows in the home folder that are locked and I can't close the error message or the window. 

This all happened when the Samsung drive partitioned itself when I plugged it in. 
I really don't know how to fix this problem. Any help will be appreciated.
Thank you.

---

### Post by TheFu on 2014-07-28
Lost+Found is put there by UNIX file systems as a place to put orphaned inodes ... er ... lost files that have been found.
Don't have any idea what DishArc is for - some included backup software that came with the HDD, perhaps?  If you don't want to use it, reformat the HDD, repartition it however you like and that should remove the DishArc stuff.

I don't understand the usershare messages. Which OS are you running?

---

### Post by Gnusboy on 2014-07-28
TheFu' 

Thanks for your response.

I'm running Ubuntu 12.04 - and itching to upgrade. I got the existing windows to close and I think the "DishArc" and "Lost+Found" files are some files leftover from a movie transfer I made from an old Dish Network receiver to a new one. What was curious, is that I transferred the movies from one TV receiver to the H/D and then to another TV receiver without problem. Then when I connected the H/D to my desktop. The three partitions that showed up were: one for 1.1 GB, another for 462 GB and a third partition for 537 GB. I did not run any partition program or make any connection other than to plug in the drive - that's just the way it happened.
All three of the new partitions (462GB + 537GB + Lost+Found) have the DishArc and Lost + Found files marked "empty" and "unreadable."  I want to know if I can delete these files and copy my Home folder for a backup.
Does this make sense to you? I'm baffled. Do you think I shout wipe the drives and repartition them before using them as is?
I appreciate any clarity you can offer.
Thanks again.

---

### Post by TheFu on 2014-07-28
Yes, you should delete all partitions from the drive.

Yes, you should create whatever partition scheme you like on the  drive.

Yes, you should format with a LINUX file system for each partition - when that is done, there will be a "lost+found" directory again.  This is required on every linux/UNIX file system in the mount point.

If you do not, then the partitioning may not be standard - DVRs are known to use odd partitioning and strange file systems. I think TiVo did this as a way to enforce added complexity and aid with DRM, but don't quote me.  My TiVo still has a 300G HDD inside it - unused for the last 4 yrs, since the DTV mandated change turned it into a paperweight.

---

