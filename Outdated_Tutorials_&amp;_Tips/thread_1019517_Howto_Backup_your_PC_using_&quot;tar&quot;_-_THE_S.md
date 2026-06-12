---
title: "Howto: Backup your PC using &quot;tar&quot; - THE SUPER PROGRAM"
date: 2008-12-23
forum: Outdated Tutorials &amp; Tips
---

### Post by nunnst on 2008-12-23
**[SIZE="5"][B]How to Backup your PC using "tar" - THE SUPER PROGRAM**[/SIZE][/B]

The "tar" command is a powerful Command Line Interface program.  It creates and extracts archive files that maintain file structure and file permissions.  It can also compress the archive file it creates using several different compression algorithms. 

This tutorial covers making a complete backup of your system that can be used to (1) restore your system to the same partition in the event of a corrupted file system and, (2) to move your system to a new partition on the same PC (or very similar PC) after a fresh install of the original release.  I have thoroughly tested each of these steps and commands and all works well on MY system, however, I cannot guarantee that it will work the same on YOUR system.   

The tutorial is split into the following sections

I.	Preparation
II.	Create a backup of your Personal Files.
III.	Update the backup of your Personal Files. 
IV.	Restoring your Personal Files.
V.	Backing up your System Files
VI.	Restoring your System Files to a corrupted file system.
VII.	Restoring your full system to a fresh distribution install.

Before we begin, a couple of questions need to be answered.  With all the backup tutorials, scripts and programs that are available through the forums, why would I write another one and why would you want to use "tar" from the command line to backup your system?  I am writing another one because (1) too much information is better than too little, (2) because many of the existing "How To's" are dated, confusing, or have conflicting information (at least from my perspective) and (3) because I believe the structure and detail of my tutorial will help others.  Most of the backup tutorials and scripts I have seen work just fine and will likely meet your needs, however, I prefer to be in total control of something as important as my backup, so I choose to use "tar" from the command line.  Also, although "tar" is powerful it is simple, making it easy to change as my needs change.   

[SIZE="4"]**I.	Preparation**[/SIZE]

[LIST=1]
[*]Make a backup plan/schedule based on YOUR needs.  If you are constantly changing your system then you should make more frequent backups.

[*]Stick to your plan/schedule  - what good is a year old backup?

[*]Ideally use an external hard drive or usb flash drive.

[*]Use CD/DVD if you must...the point is doing backups will save you in the long run.

[*]DO NOT use a partition on the drive your backing up to store your backup. If that drive crashes you've lost your backup (or at a best it will cost you a small fortune to hire a drive recovery service)  

[*]Stick to your plan/schedule - worth repeating.
[/LIST]

[SIZE="4"]**II.	Create a backup your Personal Files**[/SIZE]

Your personal files are distinct from your "system" files and it is best to back them up separately from the "system" files.    

Your personal files are never static, they change from minute-to-minute, for example, every time you visit a web site using a browser like Firefox, several files contained in your /home directory will change.  Depending on your particular goals, you may or may not want to include files like these in your back-ups.  The "tar" command has the flexibility to handle whichever choice you might make.  By making a separate archive of your /home directory you will save time and have more flexibility.

Assuming that you want to backup every file in your /home directory, the following commands would be issued from the command line.

```
~$ sudo su   (you will be prompted for your password)
  
~# cd /

/# tar -cvpf /<pathofbackupmedia>/home_backup.tar /home/<nameofuserdirectory> 
```


That's it, sit back and watch the screen go by.  When it stops, assuming no errors occurred, there will be a file under the directory you specified called "home_backup.tar".  Now you can do whatever you need to do with this file.

Note that this file is **NOT** compressed.  I could have compressed it, but I chose not to because I want to update it using tar on a regular basis, without rewriting every file.  If your using CDROM or DVD there is no real benifit to not compressing so go ahead and compress the file using the following command and then burn it to the media.

```
/# tar -cvpxf /<pathofbackupmedia>/home_backup.tgz /home/<nameofuserdirectory>

```

Because I use a separate disk to store my backups my command tells tar to write the archive to that specific drive.  The command I actually use is:

```
tar -cvpf /media/backupdisk/home_backup.tar --exclude=/home/steve/music --exclude=/home/steve/video /home/steve
```

Split-down, this command means....

1) [FONT="Courier New"]tar -cvpf [/FONT] -->  c=create a new archive, v=verbose (show activity on the the display), p=preserve my file permissions, f=write the archive to a file 

2) [FONT="Courier New"]/media/backupdisk/home_backup.tar[/FONT] -->  this tells tar where to write the archive file and what to name it.

3) [FONT="Courier New"]--exclude=/home/steve/music[/FONT] --> this tells tar NOT to include my "music" directory files in the archive.

4) [FONT="Courier New"]--exclude=/home/steve/video[/FONT] --> this tells tar NOT to include my "video" directory files in the archive.

5) [FONT="Courier New"]/home/steve[/FONT] --> this tells tar from what directory to begin making the archive.  

I already have external copies of my music and videos and therefore do not include them.  You might want to include these directories in you plan.  If so, just omit the "exclude" parameter.

Remember, once you have created your archive file using tar, you can then do whatever you want to do with it, i.e., move it to another directory, copy it to disk, or even compress it.  

[SIZE="4"]**III.	Update the backup of your Personal Files**[/SIZE]

Instead of creating a new archive of my /home directory every time I backup, I simply "update" the existing archive by issuing the following command.

```
tar -uvpf /media/backupdisk/home_backup.tar --exclude=/home/steve/music --exclude=/home/steve/video /home/steve

```

The command is virtually the same as the create archive command with one important expection  - the "-cvpf" is replaced with a "-uvpf".  The "u" tells tar to only write into the archive files that are new or that have changed since the last time the archive was touched (meaning either created or updated).

I update my /home archive daily (yes, I'm a bit anal, but when you have experienced a disk failure and lost everything you'll understand).  The choice is yours as to how often you want to update.

[SIZE="4"][B]
IV.	Restore the backup of your Personal Files[/B][/SIZE]

If you need to restore a single file, a specific directory, or all of your personal files, "tar" can handle it.

*_**To restore a single file from your backup archive use the following commands.**_*

```
~$ sudo su

~# cd /
 
/# tar -xvpf /<pathofarchivefile>/home_backup.tar <path-&-name-of-file-to-restore> 

```
A real world example is of this command would be....

```
tar -xvpf /media/backupdisk/home_backup.tar home/steve/'New Folder'/Video/document1
```

This command says....

1) [FONT="Courier New"]tar -xvpf[/FONT]  -->  x=extract from an archive, v=verbose (show activity on the the display), p=preserve the file permissions, f=write the file to the target disk 

2) [FONT="Courier New"]/media/backupdisk/home_backup.tar[/FONT] -->  this tells tar what archive file to extract from and where it is.

3) [FONT="Courier New"]home/steve/'New Folder'/Video/document1[/FONT] --> this tells tar what file to extract

**NOTE:** The path of the file being extracted does _not_ include a leading "/".  This is because tar already assumes it's starting point is "/".  Frankly, I find this a bit confusing, but the command works as shown.  If you go ahead and add the starting "/" then the command will fail and return an error.    


***_To restore an individual directory and its content from your  archive use the following commands._***

```
~$ sudo su

~# cd /
 
/# tar -xvpf /<pathofarchivefile>/home_backup.tar <path-of-target-directory>
```
 

A real world example is of this command would be....

```
tar -xvpf /media/backupdisk/home_backup.tar home/steve/'New Folder'/Video/

```

This command extracts the Video directory and its content to the path /steve/home/'New Folder'

***_To restore your whole personal file system and its content from your archive use the following commands._***

```
~$ sudo su

~# cd /
 
/# tar -xvpf /<pathofarchivefile>/home_backup.tar <start-directory-of- archive>
```

A real world example is of this command would be....

```
tar -xvpf /media/backupdisk/home_backup.tar home/
```
 
This will restore all directories under the /home directory.  Notice its the same command as above it just eliminates the subordinate directories from the parameter.


**[SIZE="4"]V.	Backing up your System Files[/SIZE]**

Backing up your "system" files is really no different that backing up your personal files, with two exceptions.  First, there are several directories in the system hierarchy that make no sense to backup.  These include but are not limited to the following

[INDENT]/home  --> used for personal files (backup separately)

/lost+found  --> used by the fsck to store result of a recovery 

/proc --> a directory of kernel processes. A virtual file system created at each boot.

/sys  --> similar to the /proc directory.  Used by the kernel and created at boot time.

/var/lock  --> used by programs to dynamically lock devices and files.

/var/run -->  contains PID files and other system info valid until next boot.[/INDENT]

Others you might not want to include in your backup are /media and /mnt directories.  These hold the mount points of your removable media and other disk drives.  If you include these directories and the devices are mounted onto the file all the files on those devices will also be backed up.

Lastly, you do not want to include the archive file you are creating in your system backup.  

The second difference between the system files backup and the personal files backup is that system archive you create will be compressed by adding the "z" parameter to the command and giving the archive file a .tgz extension instead of a .tar extension.  Because the system files change less frequently, compressing the file makes good sense.  However, you will not be able to update this compressed file with the tar program.  As such, you should make a new archive file whenever you make significant changes to you system (like upgrading to a new kernel, or adding a local application not in the repositories).   

The tar command used to create a system archive, as detailed below, addresses all of the above items.

***_To create an archive of your system files issue the following commands:_***

```
~$ sudo su

~# cd /
 
/# tar -cvpzf /<pathofbackupmedia>/sys_backup.tgz --exclude=/home --exclude=/lost+found --exclude=/proc --exclude=/sys --exclude=/var/lock --exclude=/var/run --exclude=/media --exclude=/mnt --exclude=/sys_backup.tgz /
```

**NOTE:** The above command assumes you do NOT want to backup any devices mounted in /media or /mnt. If in fact you do want to include those mounted devices then omit the exclusion statement.

The above will result in a compressed archive file being created in whatever path you selected.  


**[SIZE="4"]VI.	Restoring System Files to a corrupted file system ON THE SAME PARTITION[/SIZE]**

If your like me, you are always experimenting with you system and occasionally screw something up so badly it's not worth the effort to try and figure it out.  That's when I pull out my system files archive and restore my system using the following command.

```
~$ sudo su 

~# cd /	

/# tar -xvpzf /<pathofbackupmedia>/sys_backup.tgz -C /

```

If all goes well, then reboot.  It is common to receive a &#65279;message at the end of the process that says [COLOR="Purple"]"tar: Error exit delayed from previous errors"[/COLOR].  Don't worry about this message. 


This command will overwrite every file on your system that is in the archive.  You can do this on a running system, so no need to use a liveCD unless you've managed to render your system un-bootable.  Additionally, this command will NOT delete files that are not in the archive.  For example say you have a file named "foo-1" and "foo-2" in the "/" directory.  If your backup archive does not include "foo-2" then it will still remain after you have extracted the archive.   Actually, this can be a good thing or a it can be bad thing, all depending upon your specific situation.  I always try using this command first and if it does not clean up my system then I use this command.  

```
~$ sudo su 

~# cd /	

/# tar -xvpzf /<pathofbackupmedia>/sys_backup.tgz --recursive-unlink -C /
```

If all goes well, then reboot. It is common to receive a &#65279;message at the end of the process that says [COLOR="Purple"]"tar: Error exit delayed from previous errors"[/COLOR].  Don't worry about this message.

The --recursive-unlink parameter removes existing directories before extracting directories of the same name.  Therefore, the result is you end up with directories containing only what was in the backup archive.  Be aware if you use this command and you have not backed up in a long time, you will probably lose some programs and files that you had installed.

If you have rendered your system unbootable, you will most likely need to reinstall GRUB.  There are numerous tutorials in the forums on how to do just that.   If your GRUB setup if fine but your system hangs up and you cannot get to a command prompt then its time for a liveCD.  My experience is that if I have to use a live CD, I might as well just do a fresh install of the distribution and then restore my backup archive and personal files to the fresh install.   This is covered in the next section.

**[SIZE="4"]VII.	Restoring your full System to a fresh install of the same release on the same or a new partition.[/SIZE]**

There are numerous reasons why you might want to restore your system to a freshly installed distribution.  I will cover a couple of them in the section.  First, supposed you've hosed your system and just don't have the energy or time to try and figure out what file(s) is causing the problem.  Because you keep your archives up-to-date you can quickly get your system back to just the way you want it.  

From your fresh install desktop, open a terminal and have your backup archives handy.

Restore your home directory first.

```
~$ sudo su

~# cd /

/# tar -xvpf /<pathofbackupmedia>/home_backup.tar home/

```
Restore your system files.

```
/# tar -xvpzf /<pathofbackupmedia>/sys_backup.tgz --exclude=boot/grub --exclude=etc/fstab -C /

```

We exclude /boot/grub and etc/fstab because when you do a fresh install both of these are created specific to the UUID of your partition by the fresh install.  There is no need to restore them and not restoring them gives you the flexibility to rearrange your partitions or to switch file system formats, i.e., switch from ext3 to xfs before the fresh install.  

Reboot, login and all should be well.  Note: the initial boot might take a bit longer.

It's really that simple!  

If your moving to a new system or distribution release, these instructions might not work or they might.  It depends on several factors, i.e., same class of CPU or not, local compiles or not, etc.  There are many variables and got ya's that can pop-up and are beyond the scope of this tutorial as well as beyond my knowledge level.  If you do try it, either on a new release or new PC, you should probably exclude the /dev and /boot directories from being restored in addition to the ones already excluded in this tutorial. My suggestion is to try it and see what happens.

Best of luck and I hope someone finds this helpful.

---

### Post by logos34 on 2008-12-23
Nice tut, Nunnst! Similar to what I use.

I backup using tar regularly, using gzipped archive.  But I notice that fewer and fewer people seem to want to do anything from the CLI these days. Shame, because tar is still a great tool.

Here's a neat little trick I use to create DVD-sized slices of my gzipped backups--maybe it'll interest someone:

> cd /

sudo tar czp /media/backups/homebackup$(date +%Y%m%d).tgz  /home/user | split -d -b 4480m - /media/backups/homebackup$(date +%Y%m%d).tgz

(You can also add '--exclude=' options if you want)

This creates a gzipped archive backup of the entire /home/user directory named 'homebackup' (with date appended), split into DVD-size (DVD-5 single-layer) chunks (4480 MB, or ~4.4 GB), and placed in /media/backups directory. For CD-size, you might use '650m' or '700m'.

(~4.4 GB + leftover ~450 MB):
> -r--r--r-- 1 root root [COLOR="Red"]4697620480[/COLOR] 2008-12-14 08:09 homebackup20081214.tgz[COLOR="Red"]00[/COLOR]
-r--r--r-- 1 root root [COLOR="Red"]471414245[/COLOR] 2008-12-14 08:12 homebackup20081214.tgz[COLOR="Red"]01[/COLOR]

Then burn them to discs.

---

### Post by malel on 2008-12-23
Thank you 'nunnst'. I have been looking for something like this for a long time and it is just what I want . I have now got my 'Home' dir and complete hard drive backed up into an external HDD

Is it possible to set up a 'cron' job to run the scripts on a regular basis?

:D

Kind regards

---

### Post by nunnst on 2008-12-24
> **malel said:**
> Thank you 'nunnst'. I have been looking for something like this for a long time and it is just what I want . I have now got my 'Home' dir and complete hard drive backed up into an external HDD

Is it possible to set up a 'cron' job to run the scripts on a regular basis?

:D

Kind regards

Yes, it very possible and typical to setup as cron job. However, I have never done it so cannot guide you. :(   This is something I'll work on and make another guide (when time permits :)).

Joy that you found success using this tutorial.  Tar is such a great program!

---

### Post by nunnst on 2008-12-24
> **logos34 said:**
> Nice tut, Nunnst! Similar to what I use.

I backup using tar regularly, using gzipped archive.  But I notice that fewer and fewer people seem to want to do anything from the CLI these days. Shame, because tar is still a great tool.

Here's a neat little trick I use to create DVD-sized slices of my gzipped backups--maybe it'll interest someone:

```
cd /

sudo tar czp /media/backups/homebackup$(date +%Y%m%d).tgz /home/user | split -d -b 4480m - /media/backups/homebackup$(date +%Y%m%d).tgz 
```

(You can also add '--exclude=' options if you want)

This creates a gzipped archive backup of the entire /home/user directory named 'homebackup' (with date appended), split into DVD-size (DVD-5 single-layer) chunks (4480 MB, or ~4.4 GB), and placed in /media/backups directory. For CD-size, you might use '650m' or '700m'.

(~4.4 GB + leftover ~450 MB):

Then burn them to discs.

Very useful tip for those without separate hard drive.  :)

Thanks, I'm glad it's the first post under the tutorial!

---

### Post by moonoo on 2009-01-03
bravo!

Cracking tut!

---

### Post by generic_idea_machine on 2009-01-03
Are there any benefits of using tar over the  "Simple Backup/Restore Config" utility?

---

### Post by LouisBlank on 2010-10-28
Good going nunnst. 

Because this guide was posted some time ago, I wanted to fully test it with Lucid.  

I backed up 3 machines, 2 of which have no data to speak of - the other having most data on the second, shared 2tb drive (my main machine).  

All the backups went well, but I did get an error "file changed while we read it" on that data portion of the backup (my main machine). 

What I wanted to do is test the restore capabilities so I tried completely cloning my least critical of my machines first :

Plugged in an old hard disk (different size)
Installed Lucid fresh
Performed all updates
Restarted
Ran your tar example from the guide to restore data and system...


sudo su
cd /
tar -xvpf /<pathofbackupmedia>/home_backup.tar home/

tar -xvpzf /<pathofbackupmedia>/sys_backup.tgz --exclude=boot/grub --exclude=etc/fstab -C /



Result:

There was an error "Exiting with previous errors", but I rebooted and everything works!!  

Buenisimo!!!

Now I have an extra hard disk ready to plug in and go if something happens to my system.  


I want to repeat this for my main machine - reason being that the backup takes over 3 hours and if it dies one day, I don't have 2 hours for the install and another 3 hours for the restore during my busy work day.  

Note: I have not tried to tar the 2tb drive - since it's all data, I did a straight copy backup.  It would be interesting to do incremental backups of the smaller directories containing text, spreadsheets, etc.

---

