---
title: "Same Harddisk on Dualboot"
date: 2016-06-06
forum: New to Ubuntu
---

### Post by kaan4 on 2016-06-06
Hello,

I have 2 SSD's (1 has windows installed and other has ubuntu) and 1 hard drive. I was using the harddrive only on windows and I have my files I installed using windows on it(not the os files). I realised that I can use that hard drive when I am on Ubuntu aswell. Would that damage my data or anything? 

Thanks

---

### Post by howefield on 2016-06-06
No, you won't the "Data" drive by using it via Ubuntu, you might have issues if you mount the Windows drive (the OS drive) in Ubuntu so best not to do that.

You probably have a backup of all your important data amyway, yes ?

---

### Post by kaan4 on 2016-06-06
Yeah I am not mounting the OS drive its just a 1TB internal hard drive. So I can access the files on that and its okay, thats good to know. But I dont have a backup of my files. Should I install a backup software? Can you suggest one?

Thank you

---

### Post by oldfred on 2016-06-06
Some like full image backups like clonezilla, others like incremental backups like rsync.
With Windows an image backup may make more sense as it can be difficult to install & configure.

       discussion of alternatives/strategy backups
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)
[https://help.ubuntu.com/community/CategoryBackupRecovery](https://help.ubuntu.com/community/CategoryBackupRecovery)

I find Ubuntu easy enough to reinstall, so I do not back up system, I do backup /home, /mnt/data and any system files in /etc that I have manually maintained. When I edit something in /etc like a grub file, I then put another copy in /home so my backup of /home includes it.

Some other users that dual boot suggest Windows tools to backup Windows.

 Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)
Microsoft Windows 8.1 reinstall/refresh
[http://windows.microsoft.com/en-us/windows-8/create-reset-refresh-media](http://windows.microsoft.com/en-us/windows-8/create-reset-refresh-media)

If NTFS partition(s) are on internal drive better to permanently mount with fstab.
 [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab) 

      
 [http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Mount & edit fstab from user Morbius1 in Post # 6 - suggest using templates instead.
Good example of manually mounting, except I prefer /mnt/xxx as location to mount to.
For ntfs UUID shown is example only see below:
UUID=XXXXXXXXXXX   /media/WinD ntfs defaults,nls=utf8,umask=000,uid=1000,windows_names 0 0
Window_names prevents the use of invalid windows characters:
(which are the nine characters &#8221; * / : < > ? \ | and those whose code is less than 0×20) 
uid=1000 should fix the trash problems as well:

---

