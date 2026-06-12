---
title: "Need to Make Backup Script for Multiple Directories"
date: 2012-11-27
forum: New to Ubuntu
---

### Post by Voreskin on 2012-11-27
Hello,

I am very new at all this server stuff. I am needing to make a backup script to backup individual users home directories to a backup server on the same LAN. I need to keep a minimum of 8 backups, and backups need to happen at one hour intervals. I also need a way to restore any files the users may accidentally delete back to their home directory. I am using Ubuntu 12.04.1. Any help I could get would be greatly appreciated, I have had almost no scripting experience at all, so any pointers you could give would be great :)

Thanks!!

---

### Post by oldfred on 2012-11-27
Some places to look.

       [https://help.ubuntu.com/community/rsync](https://help.ubuntu.com/community/rsync)
[https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)

    
       Some files to exclude from /home:
[http://ubuntuforums.org/showthread.php?t=1883834](http://ubuntuforums.org/showthread.php?t=1883834)
    
Some examples:
       rsync confirmation list:
[http://ubuntuforums.org/showthread.php?t=1692800](http://ubuntuforums.org/showthread.php?t=1692800)
Check for mount of backup partition
[http://ubuntuforums.org/showthread.php?t=1701292](http://ubuntuforums.org/showthread.php?t=1701292)
#[http://ubuntuforums.org/showthread.php?t=1555647&page=4](http://ubuntuforums.org/showthread.php?t=1555647&page=4)
more scripts:
[http://ubuntuforums.org/showthread.php?t=1319155](http://ubuntuforums.org/showthread.php?t=1319155)
[http://ubuntuforums.org/showthread.php?t=1555647&page=4](http://ubuntuforums.org/showthread.php?t=1555647&page=4)

---

### Post by Voreskin on 2012-11-28
This is what i tried for a test backup. You will probably laugh when you read it, but I'm VERY new at this. Could someone take a look and tell me why I'm getting the errors i'm getting please?

```
#!/bin/bash

FILE="testbackup`date +%Y.%m.%d.%H.%M`.tgz"
FOLDER="/home/justin/"

tar czf $FOLDER > $FILE
scp $FILE jvore@10.17.4.235:/home/jvore/backups

```

Returns

```
tar: Cowardly refusing to create an empty archive
Try `tar --help' or `tar --usage' for more information.
testbackup2012.11.28.15.57.tg 100%    0     0.0KB/s   00:00 

```

Any help would be appreciated!

---

### Post by bab1 on 2012-11-28
> **Voreskin said:**
> This is what i tried for a test backup. You will probably laugh when you read it, but I'm VERY new at this. Could someone take a look and tell me why I'm getting the errors i'm getting please?

```
#!/bin/bash

FILE="testbackup`date +%Y.%m.%d.%H.%M`.tgz"
FOLDER="/home/justin/test/"

tar czf $FOLDER &gt; $FILE
scp $FILE jvore@10.17.4.235:home/jvore/backups

```

Returns

```
./backup.sh: line 6: gt: command not found
tar: ./backup.sh: line 6: testbackup2012.11.28.15.47.tgz: command not found
Cowardly refusing to create an empty archive
Try `tar --help' or `tar --usage' for more information.
testbackup2012.11.28.15.47.tgz: No such file or directory

```

Any help would be appreciated!

Why beat yourself up?  The scripts are already written for rsync.  The app/scripts is called rsnapshot.  See [**_[COLOR="Blue"]here[/COLOR]_**]("rsnapshot") for information.

Just configure it and it will do exactly what you want.

---

### Post by SeijiSensei on 2012-11-28
Just so you'll know why the tar command did not work, if you use the "f" parameter it expects the name of the tar file to follow immediately thereafter like this

```
tar czpf $FILE $FOLDER
```

You definitely need to include the "p" option to **p**reserve the ownerships, permissions, and datestamps on the files.  If you replace "z" with "j" it uses the slower to create, but more compressed bzip2 format.  If you add "v", you'll get a list of the files being stored.

If you want to see an example where multiple backups are rotated, see [this posting](http://ubuntuforums.org/showpost.php?p=10368151&postcount=3).

---

### Post by Voreskin on 2012-11-28
Thank you all! It's so nice to have a place where noobs like me can go to get some professional help! It's people like you that make Linux fun!

I will start off with the rsnapshot, and see where that gets me!

---

### Post by BlinkinCat on 2012-11-28
> **voreskin said:**
> thank you all! It's so nice to have a place where noobs like me can go to get some professional help! It's people like you that make linux fun!


+1

---

### Post by Voreskin on 2012-11-29
I have rsnapshot set up and working! The only issue I am having with it is that its naming all of the hourly backups hourly.0, hourly.1 etc. Is there a way that I can change this as I am backing up multiple servers with multiple home directories separately?

Thanks again for all the help!

---

### Post by bab1 on 2012-11-29
> **Voreskin said:**
> I have rsnapshot set up and working! The only issue I am having with it is that its naming all of the hourly backups hourly.0, hourly.1 etc. Is there a way that I can change this as I am backing up multiple servers with multiple home directories separately?

Thanks again for all the help!

Have you looked inside a hourly directory.  Each host (or directory) should have its own directory below.  I backup 6 hosts and I use a variety of names (some are hostnames and some are specific directories on on hosts).

You name the root directory when you configure the "backup points" in rsnapshot.conf.  See the snippet of my rsnapshot.conf file below.  In the first instance I have backed up my home directory on the host *rincon*.  In the second instance I am backing up a directory that is not a home directory.  It's a users data that is no longer on the system.  Both of these are on the backup server.  The third  instance is remote host that I am backing up all of the home directories.  The individual homedirs are in the subdirectories under the hostname.

The destination is  an external HDD that I rotate drives on.    ```
###############################
### BACKUP POINTS / SCRIPTS ###
###############################

# LOCALHOST
backup  /home/bab                     **[COLOR="Red"] rincon/[/COLOR]**
backup  /smb/egb_data                 **[COLOR="Red"] egb_data/[/COLOR]**
...
# REMOTE HOSTS
backup  root@malibu:/home              **[COLOR="Red"]malibu/[/COLOR]**
...

```

When you look at this under a weekly directory you see this```
drwxr-sr-x 3 root smbusers 4096 2012-05-06 16:55 rincon
drwxr-sr-x 3 root smbusers 4.0K 2012-05-06 16:55 egb_data
drwxr-sr-x 3 root smbusers 4.0K 2012-05-06 18:55 malibu

```

How have you setup the rsnapshot.conf file?  Post an hourly.0 directory listing and the rsnapshot.conf file.

If you really need to separate this more you can run separate versions of the rsnapshot.conf file.  I have done this when testing the configuration when adding a new host.

[COLOR="Blue"]Edit:  It's important to understand these backups are not a monolithic block of compressed data.  The directories are usable just like any other Linux directory.  You can look at the data directly; no special program is needed for recovering the files.[/COLOR]

---

### Post by Voreskin on 2012-11-29
Here is my rsnapshot.conf file! I did get this to work after deleting all of the hourly backups it already had, i think because it is incremental it was not changing it for me, which makes sense.

Thanks again for all the help! Time to go try it on the real servers!!:D

```
#################################################
# rsnapshot.conf - rsnapshot configuration file #
#################################################
#                                               #
# PLEASE BE AWARE OF THE FOLLOWING RULES:       #
#                                               #
# This file requires tabs between elements      #
#                                               #
# Directories require a trailing slash:         #
#   right: /home/                               #
#   wrong: /home                                #
#                                               #
#################################################

#######################
# CONFIG FILE VERSION #
#######################

config_version	1.2

###########################
# SNAPSHOT ROOT DIRECTORY #
###########################

# All snapshots will be stored under this root directory.
#
snapshot_root	/var/cache/rsnapshot/

# If no_create_root is enabled, rsnapshot will not automatically create the
# snapshot_root directory. This is particularly useful if you are backing
# up to removable media, such as a FireWire or USB drive.
#
#no_create_root	1

#################################
# EXTERNAL PROGRAM DEPENDENCIES #
#################################

# LINUX USERS:   Be sure to uncomment "cmd_cp". This gives you extra features.
# EVERYONE ELSE: Leave "cmd_cp" commented out for compatibility.
#
# See the README file or the man page for more details.
#
cmd_cp		/bin/cp

# uncomment this to use the rm program instead of the built-in perl routine.
#
cmd_rm		/bin/rm

# rsync must be enabled for anything to work. This is the only command that
# must be enabled.
#
cmd_rsync	/usr/bin/rsync

# Uncomment this to enable remote ssh backups over rsync.
#
cmd_ssh	/usr/bin/ssh

# Comment this out to disable syslog support.
#
cmd_logger	/usr/bin/logger

# Uncomment this to specify the path to "du" for disk usage checks.
# If you have an older version of "du", you may also want to check the
# "du_args" parameter below.
#
#cmd_du		/usr/bin/du

# Uncomment this to specify the path to rsnapshot-diff.
#
#cmd_rsnapshot_diff	/usr/bin/rsnapshot-diff

# Specify the path to a script (and any optional arguments) to run right
# before rsnapshot syncs files
#
#cmd_preexec	/path/to/preexec/script

# Specify the path to a script (and any optional arguments) to run right
# after rsnapshot syncs files
#
#cmd_postexec	/path/to/postexec/script

# Paths to lvcreate, lvremove, mount and umount commands, for use with
# Linux LVMs.
#
#linux_lvm_cmd_lvcreate	/sbin/lvcreate
#linux_lvm_cmd_lvremove	/sbin/lvremove
#linux_lvm_cmd_mount	/bin/mount
#linux_lvm_cmd_umount	/bin/umount

#########################################
#           BACKUP INTERVALS            #
# Must be unique and in ascending order #
# i.e. hourly, daily, weekly, etc.      #
#########################################

retain		hourly	8
retain		daily	7
retain		weekly	4
retain		monthly	3

############################################
#              GLOBAL OPTIONS              #
# All are optional, with sensible defaults #
############################################

# Verbose level, 1 through 5.
# 1     Quiet           Print fatal errors only
# 2     Default         Print errors and warnings only
# 3     Verbose         Show equivalent shell commands being executed
# 4     Extra Verbose   Show extra verbose information
# 5     Debug mode      Everything
#
verbose		2

# Same as "verbose" above, but controls the amount of data sent to the
# logfile, if one is being used. The default is 3.
#
loglevel	3

# If you enable this, data will be written to the file you specify. The
# amount of data written is controlled by the "loglevel" parameter.
#
#logfile	/var/log/rsnapshot.log

# If enabled, rsnapshot will write a lockfile to prevent two instances
# from running simultaneously (and messing up the snapshot_root).
# If you enable this, make sure the lockfile directory is not world
# writable. Otherwise anyone can prevent the program from running.
#
lockfile	/var/run/rsnapshot.pid

# By default, rsnapshot check lockfile, check if PID is running
# and if not, consider lockfile as stale, then start
# Enabling this stop rsnapshot if PID in lockfile is not running
#
#stop_on_stale_lockfile		0

# Default rsync args. All rsync commands have at least these options set.
#
#rsync_short_args	-R
#rsync_long_args	--relative

# ssh has no args passed by default, but you can specify some here.
#
#ssh_args	-p 22

# Default arguments for the "du" program (for disk space reporting).
# The GNU version of "du" is preferred. See the man page for more details.
# If your version of "du" doesn't support the -h flag, try -k flag instead.
#
#du_args	-csh

# If this is enabled, rsync won't span filesystem partitions within a
# backup point. This essentially passes the -x option to rsync.
# The default is 0 (off).
#
#one_fs		0

# The include and exclude parameters, if enabled, simply get passed directly
# to rsync. If you have multiple include/exclude patterns, put each one on a
# separate line. Please look up the --include and --exclude options in the
# rsync man page for more details on how to specify file name patterns. 
# 
#include	???
#include	???
#exclude	???
#exclude	???

# The include_file and exclude_file parameters, if enabled, simply get
# passed directly to rsync. Please look up the --include-from and
# --exclude-from options in the rsync man page for more details.
#
#include_file	/path/to/include/file
#include_file	/home/justin/
#exclude_file	/path/to/exclude/file

# If your version of rsync supports --link-dest, consider enable this.
# This is the best way to support special files (FIFOs, etc) cross-platform.
# The default is 0 (off).
#
#link_dest	0

# When sync_first is enabled, it changes the default behaviour of rsnapshot.
# Normally, when rsnapshot is called with its lowest interval
# (i.e.: "rsnapshot hourly"), it will sync files AND rotate the lowest
# intervals. With sync_first enabled, "rsnapshot sync" handles the file sync,
# and all interval calls simply rotate files. See the man page for more
# details. The default is 0 (off).
#
#sync_first	0

# If enabled, rsnapshot will move the oldest directory for each interval
# to [interval_name].delete, then it will remove the lockfile and delete
# that directory just before it exits. The default is 0 (off).
#
#use_lazy_deletes	0

# Number of rsync re-tries. If you experience any network problems or
# network card issues that tend to cause ssh to crap-out with
# "Corrupted MAC on input" errors, for example, set this to a non-zero
# value to have the rsync operation re-tried
#
#rsync_numtries 0

# LVM parameters. Used to backup with creating lvm snapshot before backup
# and removing it after. This should ensure consistency of data in some special
# cases
#
# LVM snapshot(s) size (lvcreate --size option).
#
#linux_lvm_snapshotsize	100M

# Name to be used when creating the LVM logical volume snapshot(s).
#
#linux_lvm_snapshotname	rsnapshot

# Path to the LVM Volume Groups.
#
#linux_lvm_vgpath	/dev

# Mount point to use to temporarily mount the snapshot(s).
#
#linux_lvm_mountpath	/path/to/mount/lvm/snapshot/during/backup

###############################
### BACKUP POINTS / SCRIPTS ###
###############################

# LOCALHOST
#backup	/home/		localhost/
#backup	/etc/		localhost/
#backup	/usr/local/	localhost/
#backup	/var/log/rsnapshot		localhost/
#backup	/etc/passwd	localhost/
#backup	/home/foo/My Documents/		localhost/
#backup	/foo/bar/	localhost/	one_fs=1, rsync_short_args=-urltvpog
#backup_script	/usr/local/bin/backup_pgsql.sh	localhost/postgres/
# You must set linux_lvm_* parameters below before using lvm snapshots
#backup	lvm://vg0/xen-home/	lvm-vg0/xen-home/

# EXAMPLE.COM
#backup_script	/bin/date "+ backup of example.com started at %c"	unused1
#backup	root@example.com:/home/	example.com/	+rsync_long_args=--bwlimit=16,exclude=core
#backup	root@example.com:/etc/	example.com/	exclude=mtab,exclude=core
#backup_script	ssh root@example.com "mysqldump -A > /var/db/dump/mysql.sql"	unused2
#backup	root@example.com:/var/db/dump/	example.com/
#backup_script	/bin/date	"+ backup of example.com ended at %c"	unused9
backup	justin@192.168.1.127:/home/justin/	justin/
# CVS.SOURCEFORGE.NET
#backup_script	/usr/local/bin/backup_rsnapshot_cvsroot.sh	rsnapshot.cvs.sourceforge.net/

# RSYNC.SAMBA.ORG
#backup	rsync://rsync.samba.org/rsyncftp/	rsync.samba.org/rsyncftp/

```

---

### Post by bab1 on 2012-11-29
> **Voreskin said:**
> ... I did get this to work after deleting all of the hourly backups it already had, i think because it is incremental it was not changing it for me, which makes sense.

Thanks again for all the help! Time to go try it on the real servers!!:D


I see that you have this as the only subdirectory of the various backups.
[CODEbackup	justin@192.168.1.127:/home/justin/	justin/[/CODE]

Not to hard to find the directory ```
/var/cache/rsnapshot/hourly.0/justin/

```

Post here if you need more help.

---

