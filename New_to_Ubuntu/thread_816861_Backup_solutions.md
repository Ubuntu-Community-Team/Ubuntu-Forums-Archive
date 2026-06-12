---
title: "Backup solutions"
date: 2008-06-03
forum: New to Ubuntu
---

### Post by rossmoore on 2008-06-03
Hi,

I'd like a backup solution. Ideally it would be:
[LIST=1]
[*]Like Time Machine for Apple
[*]Not thrash my disk as it scans for changes too much
[*]Notice when my USB hard drive is not attached and delay a backup until it is
[*]Notice when my USB hard drive is not attached and not throw [EDITED: I can't spell] files at the empty /media/250Gb_backup folder that is not attached to a device
[/LIST]

I've had a look at TimeVault, but it seemed to like doing point 4 above.
I've had a look at Flyback, but haven't installed it. It's lack of iNotify support implied point 2 might apply, but I don't know how bad it is. Anyone with any experience of it? Do you know if it is being actively developed to include iNotify support?

The other option is using rsync or similar with cron, but I'm new to both of those and too nervous to rely on them for something as important as backups of all my photos, documents and music.

If anyone can assuage my fears on the above points for a GUI solution like TimeVault or Flyback, or something else, then that would be great.

If anyone can talk me through using rsync and cron then that would also be great, although the GUI solution would be best.

Thanks,
Ross

---

### Post by canthus13 on 2008-06-03
I just happened across this the other day:  [Time Vault]("https://launchpad.net/timevault/+download"), which is supposed to be Time Machine for Linux.

--Me

Never mind.  I can't read. :D

---

### Post by rossmoore on 2008-06-03
Yes, I liked the look of TimeVault, and I only just came across it the other day too. Have you tried it? I'm not sure if I'm just using it wrong, or should set something to allow me only get it backing up when I hit go ('cos I know when the drive is connected, even if TimeVault doesn't).

---

### Post by canthus13 on 2008-06-03
Hmm.. Timevault DOES seem to know when the backup server is available... I would think that it would be able to figure out whether or not a removable drive is present.

--Me

I just noticed the removable drive bug in the list.  That could be a big pain in the butt to deal with.

---

### Post by rossmoore on 2008-06-03
Ooh, have you got a link to the bug list, I didn't see that. Now I can watch and wait for the bug to be fixed... And add my vote for it to be fixed. At least it's an acknowledged bug.

---

### Post by canthus13 on 2008-06-03
[https://bugs.launchpad.net/timevault/+bug/191681]("https://bugs.launchpad.net/timevault/+bug/191681")

That's the link directly to the bug report.

--Me

---

### Post by rossmoore on 2008-06-03
Thanks, canthus13. There's good discussion and progress on fixing it at least in that bugtrack.

While I wait for that to be fixed, does anyone have experience of Flyback, or another backup solution? Is Simple Backup worth trying, or does it too have significant shortcomings?

---

### Post by hyper_ch on 2008-06-03
I just like my rsync / hardlinks solution... have full backups back for 90 days is conforting ;)

---

### Post by BandD on 2008-06-03
I use Grsync, the GUI to rsync.  I don't have it set up to automatically run in any way...but I imagine it wouldn't be too hard to cron or script.  

I can vouch for it's trustworthiness.  I've never had any problems with it.

---

### Post by rossmoore on 2008-06-03
hyper_ch - your rsync / hardlinks solution sounds like what Timevault and Flyback and both trying to achieve, but with a load of GUI, friendliness and automation thrown in. Can you describe your setup, and whatever batch / rsync code you used, please?

BandD - maybe I'll use Grsync until TimeVault is in a more robust state. Thanks for the suggestion and your vote of confidence in it. I think TimeVault and Flyback, with their Time Machine like setup, are definitely the way I want things to be set up when they're ready for the mainstream.

---

### Post by hyper_ch on 2008-06-03
it's just a single shell script that I use :)

backup.sh
```

#!/bin/bash
unset PATH

# USER VARIABLES
BACKUPDIR=/backup                               # Folder on the backup server where the backups shall be located
EXCLUDES=/backup/exclude_list                   # File containing the excluded patterns
DAYS=90                                         # The number of days after which old backups will be deleted


# PATH VARIABLES
SH=/bin/sh                                      # Location of the bash bin in the production server!!!!

CP=/bin/cp;                                     # Location of the cp bin
FIND=/usr/bin/find;                             # Location of the find bin
ECHO=/bin/echo;                                 # Location of the echo bin
MK=/bin/mkdir;                                  # Location of the mk bin
SSH=/usr/bin/ssh;                               # Location of the ssh bin
DATE=/bin/date;                                 # Location of the date bin
RM=/bin/rm;                                     # Location of the rm bin
GREP=/bin/grep;                                 # Location of the grep bin
RSYNC=/usr/bin/rsync;                           # Location of the rsync bin
TOUCH=/bin/touch;                               # Location of the touch bin
DF=/bin/df;

##                                                      ##
##      --       DO NOT EDIT BELOW THIS HERE     --     ##
##                                                      ##

# CREATING NECESSARY FOLDERS
$MK $BACKUPDIR
CURRENT=$BACKUPDIR/current
OLD=$BACKUPDIR/old
$MK $CURRENT
$MK $OLD
# CREATING CURRENT DATE / TIME
NOW=`$DATE '+%Y-%m'-%d_%H:%M`
NOW=$OLD/$NOW
$MK $NOW

# RUN MYSQL BACKUP
$SH /backup/my.sh

# RUN RSYNC INTO CURRENT
$RSYNC                                                  \
        -aplvz --delete --delete-excluded               \
        --exclude-from="$EXCLUDES"                      \
        /                                               \
        $CURRENT;


# UPDATE THE MTIME TO REFELCT THE SNAPSHOT TIME
$TOUCH $BACKUPDIR/current
# MAKE HARDLINK COPY
$CP -al $CURRENT/* $NOW

# REMOVE OLD BACKUPS
for FILE in "$( $FIND $OLD -maxdepth 1 -type d -mtime +$DAYS )"
do
        $RM -Rf $FILE
#       $ECHO $FILE
done

$DF

exit 0

```

my.sh
```

#!/bin/bash
# Remove old file
mkdir /mysql_backup
rm -f /mysql_backup/*

#Dump new files
USER=*************
PASSWORD=*************
HOST=localhost

for i in $(echo 'SHOW DATABASES;' | mysql -u$USER -p$PASSWORD -h$HOST|grep -v '^Database$'); do
  mysqldump                                                     \
  -u$USER -p$PASSWORD -h$HOST                                   \
  -Q -e -C --add-drop-table --add-locks --quick --lock-tables   \
  -B $i                                                         \
  $i > /mysql_backup/$i.sql;
done;

```

exclude_list
```

/backup/current/
/backup/old/
/backup/test/
/bin/
/boot/
/dev/
/initrd/
/lib/
/lost+found/
/media/
/mnt/
/proc/
/sbin/
/sys/
/tmp/
/usr/
/var/backups/
/var/cache/
/var/local/
/var/lock/
/var/log/
/var/mail/
/var/opt/
/var/spool/
/var/tmp/

```

The mysql backup is done in a seperate file for some reasons of mine. But there is no reason why it can't be in the backup file itself.

---

### Post by rossmoore on 2008-06-03
Thanks, hyper_ch, very helpful. You've commented out the hardlinks bit - is that for a specific reason? I presume that's the bit that allows full snapshots to be taken of the system without duplication lots of data - rsync just copies the deltas, and then the full snapshot is created using cp -al, without duplicating the data.

Of course, this doesn't quite work when you delete a file - it'll still be copied forward into the latest snapshot, no? It's definitely a good and useful solution though, thanks for posting it.

---

### Post by hyper_ch on 2008-06-03
> **rossmoore said:**
> You've commented out the hardlinks bit - is that for a specific reason?
Yes, I did alter a few things yesterday and commented it out for testing... so it's uncommented again ;)

> **rossmoore said:**
> I presume that's the bit that allows full snapshots to be taken of the system without duplication lots of data - rsync just copies the deltas, and then the full snapshot is created using cp -al, without duplicating the data.
Yes, that's how it works

> **rossmoore said:**
> Of course, this doesn't quite work when you delete a file - it'll still be copied forward into the latest snapshot, no?
It will be deleted... it will existe in the older snapshots but not in the current one. First I rsync with --delete hence deleted files will get deleted there... on then I make a hardlink copy of current....

Once the 90 days are over, the file is gone.

---

### Post by rossmoore on 2008-06-03
Oh, I see. That's helped me understand cp and rsync a whole lot better. I might try something similar myself until those GUI tools get finished then. Thanks for your help!

---

### Post by Twizzle on 2008-06-10
Should the backup script be run as root? 

I have been messing around with hyper_ch's script above and it run's ok but I get a number of errors complaining about permissions. I don't want to just try running as sudo incase it screws my system (I can't quite see how it would, but don't want to risk it!).

Also, I have been reading about hardlinks from [this]("http://blog.interlinked.org/tutorials/rsync_time_machine.html") site and am a bit confused. Does the above script use them or does it create full copies of the backup each time (and so use a lot of space)

My version of the above script is as follows:

```
#!/bin/bash
unset PATH

# USER VARIABLES
MUSICDIR=/home/john/Music				# Location of Music
PICTUREDIR=/home/john/Pictures				# Location of Pictures
MUSICBAK=/home/john/SERVER/Data/			# Folder for music backup
PICTUREBAK=/home/john/SERVER/Data/			# Folder for pictures backup
BACKUPDIR=/home/john/SERVER/backup			# Folder on the backup server where the backups shall be located
EXCLUDES=/home/john/SERVER/backup/exclude_list		# File containing the excluded patterns
DAYS=30							# The number of days after which old backups will be deleted


# PATH VARIABLES
SH=/bin/sh				# Location of the bash bin

CP=/bin/cp;				# Location of the cp bin
FIND=/usr/bin/find;			# Location of the find bin
ECHO=/bin/echo;				# Location of the echo bin
MK=/bin/mkdir;				# Location of the mk bin
SSH=/usr/bin/ssh;			# Location of the ssh bin
DATE=/bin/date;				# Location of the date bin
RM=/bin/rm;				# Location of the rm bin
GREP=/bin/grep;				# Location of the grep bin
RSYNC=/usr/bin/rsync;			# Location of the rsync bin
TOUCH=/bin/touch;			# Location of the touch bin
DF=/bin/df;

##                                                      ##
##      --       DO NOT EDIT BELOW THIS HERE     --     ##
##                                                      ##

# CREATING NECESSARY FOLDERS
$MK $BACKUPDIR
CURRENT=$BACKUPDIR/current
OLD=$BACKUPDIR/old
$MK $CURRENT
$MK $OLD
# CREATING CURRENT DATE / TIME
NOW=`$DATE '+%Y-%m'-%d_%H:%M`
NOW=$OLD/$NOW
$MK $NOW

#Check and sync Music
$RSYNC							\
	--archive --fuzzy --delete-after		\
	$MUSICDIR					\
	$MUSICBAK;

#Check and sync Pictures
$RSYNC							\
	--archive --fuzzy --delete-after		\
	$PICTUREDIR					\
	$PICTUREBAK;

#Full backup into /Current
$RSYNC							\
	-aplv --delete --delete-excluded		\
	--exclude-from="$EXCLUDES"			\
	/						\
	$CURRENT;


# UPDATE THE MTIME TO REFELCT THE SNAPSHOT TIME
$TOUCH $BACKUPDIR/current
# MAKE HARDLINK COPY
$CP -al $CURRENT/* $NOW

# REMOVE OLD BACKUPS
##for FILE in "$( $FIND $OLD -maxdepth 1 -type d -mtime +$DAYS )"
##do
##	$RM -Rf $FILE
##	$ECHO $FILE
##done

##$DF

exit 0
```

---

### Post by rossmoore on 2008-06-11
Hi Twizzler,

Yes, the script uses hard links. It does a regular rsync, and then the -l option on cp makes hardlink copies. Hardlinks are a bit subtle, I'll try and explain:

The data for my picture is stored in a some random spot on my hard drive. The fact that I see the picture in the directory ~/Pictures is because the filesystem has a hardlink in that directory pointing at my picture. I can manually create a hardlink, in some other directory (say ~/Desktop), also pointing at my picture. There's no duplication of data - if I alter the picture by opening it ~/Pictures and using Picasa to rotate it, the picture is rotated. It will look rotated regardless of whether I look at it in ~/Pictures or ~/Desktop - it's the SAME file. If I delete the picture in ~/Pictures, the picture will still be there in ~/Desktop. That's because the delete command just removes the hardlink. The filesystem does not regard a bit of space on the hard drive as empty until there are 0 hardlinks to it. If I delete the hardlink in ~/Desktop - then the file is deleted. Well, actually it's still there until the filesystem overwrites that location, but I have no easy way of finding it any more.

The script does not have to be run as root. I'm not sure what problems you're having - it kind of implies that some of the files you're trying to back up are owned by root. The -a option on cp, and I think rsync itself, both preserve permissions - but you can't assign permissions to files that you don't have permission to assign. Do you have multiple users on your machine, both with write-access to you home drive? That could cause the problem I guess.

---

### Post by Twizzle on 2008-06-11
Thankyou - that does make it a bit clearer. From that I assume that if I just delete my '/current' folder and contents from the backup location, the '/old' backups will still be there as such as '/current' has not pysically gone. In fact as I typed that it made more sense too!

As for my errors, there is only one user on the computer - me and no other accounts (other than root etc). I have CTRL-C as quickly as I can after running the script to try and capture the errors (they seemed to scroll up the terminal too fast to read and more than I can scroll back) and this is the start of it:

```
john@office:~$ /home/john/backup.sh
/bin/mkdir: cannot create directory `/home/john/SERVER/backup': File exists
/bin/mkdir: cannot create directory `/home/john/SERVER/backup/current': File exists
/bin/mkdir: cannot create directory `/home/john/SERVER/backup/old': File exists
building file list ... rsync: opendir "/home/john/.dbus" failed: Permission denied (13)
rsync: opendir "/home/lost+found" failed: Permission denied (13)
rsync: opendir "/root/.dbus" failed: Permission denied (13)
rsync: opendir "/root/.config" failed: Permission denied (13)
rsync: opendir "/root/.synaptic" failed: Permission denied (13)
rsync: opendir "/root/.gnome2_private" failed: Permission denied (13)
rsync: opendir "/root/.gnome2" failed: Permission denied (13)
rsync: opendir "/root/.gvfs" failed: Permission denied (13)
rsync: opendir "/root/.loki" failed: Permission denied (13)
rsync: opendir "/root/.aptitude" failed: Permission denied (13)
rsync: opendir "/root/.gconf" failed: Permission denied (13)
rsync: opendir "/root/.googleearth" failed: Permission denied (13)
rsync: opendir "/root/.gconfd" failed: Permission denied (13)
rsync: opendir "/root/.nautilus/metafiles" failed: Permission denied (13)
rsync: opendir "/var/lib/PolicyKit" failed: Permission denied (13)
rsync: opendir "/var/lib/gdm" failed: Permission denied (13)
rsync: opendir "/var/run/sudo" failed: Permission denied (13)
rsync: opendir "/var/run/samba/winbindd_privileged" failed: Permission denied (13)
rsync: opendir "/var/run/cups/certs" failed: Permission denied (13)
rsync error: received SIGINT, SIGTERM, or SIGHUP (code 20) at rsync.c(271) [receiver=2.6.9]
rsync: writefd_unbuffered failed to write 3599 bytes [sender]: Broken pipe (32)
rsync: connection unexpectedly closed (8 bytes received so far) [sender]
rsync error: received SIGINT, SIGTERM, or SIGHUP (code 20) at io.c(454) [sender=2.6.9]

```

And if I let it run, I get lots of these errors which I think is when it is creating the '/old' hardlinks?

```
/bin/cp: cannot create link `/home/john/SERVER/backup/old/2008-06-11_15:12/var/lib/defoma/gs.d/dirs/fonts/ae_Electron.ttf': No such file or directory
/bin/cp: cannot create link `/home/john/SERVER/backup/old/2008-06-11_15:12/var/lib/defoma/gs.d/dirs/fonts/Courier_New_Italic.ttf': No such file or directory
/bin/cp: cannot create link `/home/john/SERVER/backup/old/2008-06-11_15:12/var/lib/defoma/gs.d/dirs/fonts/p052024l.pfb': No such file or directory
/bin/cp: cannot create link `/home/john/SERVER/backup/old/2008-06-11_15:12/var/lib/defoma/gs.d/dirs/fonts/ae_Arab.ttf': No such file or directory
/bin/cp: cannot create link `/home/john/SERVER/backup/old/2008-06-11_15:12/var/lib/defoma/gs.d/dirs/fonts/Verdana.ttf': No such file or directory
/bin/cp: cannot create link `/home/john/SERVER/backup/old/2008-06-11_15:12/var/lib/defoma/gs.d/dirs/fonts/n019023l.pfb': No such file or directory
/bin/cp: cannot create link `/home/john/SERVER/backup/old/2008-06-11_15:12/vmlinuz': No such file or directory
/bin/cp: cannot create link `/home/john/SERVER/backup/old/2008-06-11_15:12/vmlinuz.old': No such file or directory


```

I understand about not having certain access to /root but all I want to do is back it up otherwise there is no point in doing a system backup really.

---

### Post by rossmoore on 2008-06-11
Hmm. Those first 3 errors are fine, about it not being able to create the directory - it already exists, so no problem. The script could probably be neater if it were to detect the presence of the directories before trying to create them, but no problem.

After that you're getting some odd errors. Why is rsync trying to backup /var/lib/PolicyKit, or /home/john/.dbus? You've only asked for ~/Music and ~/Pictures.

Or is your last rsync command really trying to back up the root filesystem? If that's the case then it's presumably going to have to run as root because it will be accessing all sorts of files. Do you get the errors when you're only trying to back up Music and Pictures? Do you really want to back up the entire root filesystem - and if so would you be better off taking a compressed snapshot of the partition?

---

### Post by Twizzle on 2008-06-11
The /Music and /Pictures bit works fine (as far as I can tell) and yes the last rsync command is to back up the whole filesystem.

I basically added / tweaked the script previously posted as I want to kepp a regular sync for my photos and music but **also** want to have the file system backed up so I can:
1) do a full restore if the system goes belly up and
2) have the last 30 days of files available (I have been known to accidently delete the odd document of my wifes when 'rearranging' my setup!)

The reason I liked this method against a compressed snapshot is so I can easily access the odd file if need be (eg a document from /home/john/documents) without having to un compress a large file (forgive me if I am getting it wrong here and if you can suggest a better method I am open to ideas / help :) )

---

### Post by rossmoore on 2008-06-11
I'm no backup pro. I'd suggest you post a new thread for backing up the actual installation. Presuming your documents and data either go somewhere in home or in a separate data directory you'll be best off backing up those as you do Music and Pictures. That way accidental deletes of your wife's docs are easily recovered too. I store everything in either ~/Documents, ~/Music, ~/Pictures or ~/Videos, with sub-directories under that as necessary. Anything on the desktop is at the owner's risk.

Backing up the actual installation is another matter as you need to preserve the root nature of the installation. You'll have to run that backup as root, and may need to use something like the command cpio - I don't know how rsync handles things like devices in /dev, where all your hardwear is mapped through. I can see what you want to do (have the potential for winding back your entire installation to a previous days' version), but I have no idea how to do it, or even if it can be reliably done.

Good luck!

---

### Post by Twizzle on 2008-06-11
Thanks for your help. Ill do a bit more digging / googling before I start another thread.

---

### Post by mdpalow on 2008-06-16
QuickStart is another back-up option you can take a look at if you're interested.

It'll do tar, rsync, and image back-ups of both Ubuntu and Windows if you're dual booting.

See link in my signature for more info.

Good luck to you.

---

