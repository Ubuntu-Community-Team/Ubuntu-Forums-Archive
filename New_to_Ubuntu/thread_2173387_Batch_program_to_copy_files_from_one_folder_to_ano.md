---
title: "Batch program to copy files from one folder to another folder"
date: 2013-09-09
forum: New to Ubuntu
---

### Post by vpy-1982 on 2013-09-09
I am very new to Linux.

This is what I am trying to achieve.

a) I have two folders SRC and DESTINATION.
   SRC contains several subdirectories and files in it.


b) A batch file should be built upon clicking it the following should be done

                      b -> 1) Delete all contents from DESTINATION folder

                      b -> 2) Copies all the files/subdirectories from SRC  to DESTINATION

Can someone help me with this ?.

If this activity requires significant effort (I don’t know whether the above is simple to implement or not), do point me some resources for me to dig into it

---

### Post by oldfred on 2013-09-09
I use rsync for backup, but do not delete on the backup folder, see --delete in man page. You also can use the cp. 
man rsync
man cp
But the man on rsync is so complex as it has so many options I just found several examples and used that to start with.
What format are partitions? If not LInux you can have permission issues it copying to Windows formats like NTFS.

With rsync you can make it run as a dry run to see what it will copy use -n option.

 Originally Posted by MountainX View Post #20 also other backup apps
[http://ubuntuforums.org/showthread.php?t=868244&highlight=backup](http://ubuntuforums.org/showthread.php?t=868244&highlight=backup)
Sample rsync file, use a text editor and paste into a file & name it mybackup.sh

   -l: copies symlinks as symlinks
-t: preserves modification times
-D: preserves device and special files

  ```
 #!/bin/bash
# backup script
# a - archive, retain file settings equals -rlptgoD (no -H,-A,-X)
# r - recursive / subdirectories
# u - update, only newer
# v - verbose
# P - keep partial files and report progress
echo "starting..."
rsync -aruvP /mnt/data_DT/Documents /usr/local/fred/data/

   #rsync -auvP /home /media/backup

echo "done"
exit 0


```   make it executable
chmod +x mybackup.sh

   run it
./mybackup.sh

More info & options
[http://ubuntuforums.org/showthread.php?t=1319155](http://ubuntuforums.org/showthread.php?t=1319155)
 [https://help.ubuntu.com/community/rsync](https://help.ubuntu.com/community/rsync)
[https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)

---

