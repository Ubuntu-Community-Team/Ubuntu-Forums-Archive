---
title: "BASH shell shell script for BackupPC - please critique"
date: 2007-08-20
forum: Programming Talk
---

### Post by sacherjj on 2007-08-20
I've been  learning Ubuntu for the last 6 months and this is my first bash script.  I wanted to get feedback if there is something I should do differently.  I have setup a few Ubuntu machines for family and friends.  The main role is for running BackupPC for backing up all their PCs, but they are also used as desktop machines if needed.  The users are just learning Ubuntu and Linux and are Windows users.

This script will copy the data that BackupPC stores to allow the user to take a hard drive offsite for a second backup.  I am using this [hot-swappable SATA bay](http://www.newegg.com/product/product.asp?item=N82E16817998020). I am also backing up the config files.

```
#!/bin/bash
#
# This script was created to duplicate the /var/lib/backuppc directory
# used to store all the backup files for BackupPC.  This is used with
# a removable and hot swappable SATA drive bay to make backups that
# can be taken offsite.
#
# Created by Joe Sacher  joe@joesacher.com
#
# May be freely distributed and modified as need, as long as properly attributed.
#

script_name="createoffsite"

# Must run as root so that we can shutdown backuppc and mount drives 
if [ $(whoami) != "root" ]; then
	echo "You need to run this script as root."
	echo "Use 'sudo ./$script_name' then enter your password when prompted."
	exit 1
fi

echo "Insert offsite backup drive if you have not done so."
echo ""

# Destination mount and device
mount_point="/mnt/offsite_backup"
dest_drive="/dev/hdd1"

# Directory to copy to destination
source_path="/var/lib/backuppc"

# Source Config Directory
config_src="/etc/backuppc"

# Destination Config BackupPC
config_dest="/etc_backup"

# Backup name is 4 digit year and day of year  ex: 2007-232
backup_name=`date +%Y`-`date +%j`

# Check if the mount point exists (it shouldn't)
if [ -d "$mount_point" ]; then
	echo "Destination mount point: $mount_point already exists."
	echo "Please remove directory and rerun this $script_name."
	exit 1
fi

# Verify that the destination drive isn't mounted and unmount if desired.
# mount returnsall drives mounted, if grep finds the destination drive it is mounted
if mount | grep $dest_drive > /dev/null; then
	echo "Destination drive ($dest_drive) is already mounted."
	read -p "Unmount and continue (y/n)?"
	if [ $REPLY != "y" ]; then
		echo "Exiting..."
		exit 1
	fi
	
	umount $dest_drive 
fi

# Verify that the user wants to wipe the destination drive
echo "The destination drive will be formatted."
echo "All data on the drive will be lost!"
read -p "Continue (y/n)?"
if [ $REPLY != "y" ]; then
	echo "Exiting..."
	exit 1
fi

# Format destination drive (faster than delete, as this will have TONS 
# of files if is a used backup drive)
echo "Formatting destination drive: $dest_drive"
if ! mke2fs -j $dest_drive; then
	echo "Error formatting destination drive, exiting..."
	exit 1
fi

# Mount the drive
echo "Mounting destination drive to $mount_point"
if ! mkdir $mount_point; then
	echo "Error creating mount point directory: $mount_point, exiting..."
	exit 1
fi

if ! mount -t ext3 $dest_drive $mount_point; then
	echo "Error mounting destination drive, exiting..."
	exit 1
fi

# Shutdown backuppc
echo "Shutting down BackupPC..."
if ! /etc/init.d/backuppc stop; then
	echo "Unable to shutdown backuppc, exiting..."
	exit 1
fi

# Copy files preserving permissions, etc.
echo "Copying files..."
if ! cd $source_path; then
	echo "Unable to change into source directory: $source_path, exiting..."
	exit 1
fi
find . -depth -print0 | cpio --null --sparse -pvd $mount_point

# Create directory for backingup BackupPC config_src
if ! mkdir $mount_point$config_dest; then
	echo "Unable to make directory on destination to backup config: $mount_point$config_dest, exiting..."
	exit 1
fi

if ! cd $config_src; then
	echo "Unable to change into config directory: $config_src, exiting..."
	exit 1
fi
find . -depth -print0 | cpio --null --sparse -pvd $mount_point$config_dest

# Startup backuppc
echo "Completed backup, starting BackupPC..."
if ! /etc/init.d/backuppc start; then
	echo "BackupPC was not started correctly!"
fi

# Create an empty file with Year and Day of Year for the backup
# this is just in case the label is removed from media.
touch $mount_point/$backup_name

# Unmount and cleanup
if ! umount $dest_drive; then
	echo "Unable to unmount $dest_drive!"
	exit 1
fi

# Remove mount point directory
if rmdir $mount_point; then
	echo "Process complete, you may now eject the offsite backup drive."
	# Label drive with 4 digit year - day of year
	echo "Label this drive: '$backup_name' ([Year]-[DayOfYear])"
else
	echo "Unable to remove mount location: $mount_point!"
fi

```

Thanks for taking the time to look at it.

Joe

---

### Post by Mr. C. on 2007-08-20
This is a very thorough bash script for a first !  Nice work.

Consider catching the  user interrupting the script with Control-C or similar.    If you want to catch interrupts, see the **trap** bash built-in.  Otherwise, a user who Control-C's while the drive is mounted may just remove the mounted device; this will cause real problems.

You can use grep -q instead of grep > /dev/null.

It is clearer if you do not include the leading slash in your variables such as $config_dest.  Instead, add it when you do your variable assignments or interpolations, such as:

```
config_dest="etc_backup"
$mount_point/$config_dest
```

Consider using a function such as:

```
function die ( ) {
   echo $@
   exit 1
}
```

which allows you to reduce:

```
	if [ $REPLY != "y" ]; then
		echo "Exiting..."
		exit 1
	fi
```

to 

```
[ "$REPLY" == y ] || die "Exiting..."
```

In either case, quote REPLY, since the user could just press Enter, and REPLY will be empty (and you'll get a unary operator error from test).

MrC

---

### Post by sacherjj on 2007-08-21
Good stuff.  Thanks for the reply.  I'm reworking an will repost when completed.

---

### Post by s1ightcrazed on 2007-08-21
Not sure what your requirements are for logging, but I have always done some sort message capture so that I have a log of what the script did for afterwards. 

*NOT* having a log of what a script that YOU WROTE just did may, for some people, lead to a RGE. 

That would be a 'resume generating event', for those not in the industry.

---

### Post by sacherjj on 2007-08-21
Here is the reworked script:

```

#!/bin/bash
#
# This script was created to duplicate the /var/lib/backuppc directory
# used to store all the backup files for BackupPC.  This is used with
# a removable and hot swappable SATA drive bay to make backups that
# can be taken offsite.
#
# Created by Joe Sacher  joe@joesacher.com
#
# May be freely distributed and modified as needed, 
# as long as proper credit is given.
#

########################
# Start of user config #
########################

# Destination mount and device
mount_point="/mnt/offsite_backup"
dest_drive="/dev/hdd1"  # <- Probably only need to change this

# Source directory to copy to destination
source_path="/var/lib/backuppc"

# Source Config Directory
config_src="/etc/backuppc"

# Destination Config BackupPC
config_dest="etc_backup"

######################
# End of user config #
######################

# Should match the filename of this script
script_name="createoffsite"

# Backup name is 4 digit year and day of year.  Ex: 2007-232
backup_name=`date +%Y`-`date +%j`

function die()
{
	echo "$@"
	exit 1
}

function cleanUpMounting()
{
	echo "Cleaning up..."
	
	# Unmount drive, if mounted
	if mount | grep -q $dest_drive; then
		# Force the unmount, as the user will be ejecting the drive
		umount -f $dest_drive
	fi

	# remove mount point
	if [ -d "$mount_point" ]; then
		rmdir "$mount_point"
	fi

	# Remove trap so EXIT doesn't fire	
	trap - INT TERM EXIT

	# Must exit or will resume at place Signal occured
	echo "Exiting..."
	exit 1	
}

# Must run as root so that we can shutdown backuppc and mount drives 
[ $(whoami) == "root" ] || die "You need to run this script as root.  Use 'sudo ./$script_name' then enter your password when prompted."

# Check if the mount point exists (it shouldn't)
[ ! -d "$mount_point" ] || die "Destination mount point: $mount_point already exists.  Please remove directory and rerun this $script_name."

# Verify that the destination drive isn't mounted and unmount if desired.
# mount returnsall drives mounted, if grep finds the destination drive it is mounted
if mount | grep -q $dest_drive; then
	echo "Destination drive ($dest_drive) is already mounted."
	read -p "Unmount and continue (y/n)?"
	[ "$REPLY" == "y" ] || die "Exiting..."
	
	umount $dest_drive
fi

echo -e "Insert offsite backup drive if you have not done so.\n"

# Verify that the user wants to wipe the destination drive
echo "The destination drive ($dest_drive) will be formatted."
echo "All data on the drive will be lost!"
read -p "Continue (y/n)?"
[ "$REPLY" == "y" ] || die "Exiting..."

trap cleanUpMounting INT TERM EXIT

# Format destination drive (faster than delete, as this will have TONS 
# of files if is a used backup drive)
echo "Formatting destination drive: $dest_drive"
mke2fs -j $dest_drive || die "Error formatting destination drive, exiting..."

# Mount the drive
echo "Mounting destination drive to $mount_point"
mkdir $mount_point || die "Error creating mount point directory: $mount_point, exiting..."
mount -t ext3 $dest_drive $mount_point || die "Error mounting destination drive, exiting..."

# Shutdown backuppc
echo "Shutting down BackupPC..."
/etc/init.d/backuppc stop || die "Unable to shutdown backuppc, exiting..."

# Copy files preserving permissions, etc.
echo "Copying files..."
cd $source_path || die "Unable to change into source directory: $source_path, exiting..."
find . -depth -print0 | cpio --null --sparse -pvd $mount_point

# Create directory for backingup BackupPC config_src
mkdir $mount_point/$config_dest || die "Unable to make directory on $dest_drive to backup config: $mount_point/$config_dest, exiting..."

cd $config_src || die "Unable to change into config directory: $config_src, exiting..."
find . -depth -print0 | cpio --null --sparse -pvd $mount_point/$config_dest

# Startup backuppc
echo "Completed backup, starting BackupPC..."
/etc/init.d/backuppc start || echo "BackupPC was not started correctly!"

# Create an empty file with Year and Day of Year for the backup
# this is just in case the label is removed from media.
touch $mount_point/$backup_name

# Unmount and cleanup
umount $dest_drive || die "Unable to unmount $dest_drive!"

# Remove mount point directory
if rmdir $mount_point; then
	echo "Process complete, you may now eject the offsite backup drive."
	# Label drive with 4 digit year - day of year
	echo "Label this drive: '$backup_name' ([Year]-[DayOfYear])"
else
	echo "Unable to remove mount location: $mount_point!"
fi

# Reset trap so not called on exit
trap - INT TERM EXIT
exit 0

```

s1ightcrazed - I had not thought about logging.  This will be run by people who wouldn't think to check it, but I could see how telling them to send me the log could help remote debugging.  I'm not familiar with "resume generating event" and will do some searching.

I found a good page on [Writing Robust Shell Scripts](http://www.davidpashley.com/articles/writing-robust-shell-scripts.html) that includes how to use trap.

---

### Post by s1ightcrazed on 2007-08-21
It's an old joke. 

For instance, dropping a database while not having a backup might be a resume generating event. 

I.E:  I have just been fired - I now need to generate a new resume to look for another job. :lolflag:

---

### Post by Mr. C. on 2007-08-21
Looks pretty good!

This will cause problems if the error occurs.  The script exits without un-mounting.

```
# Shutdown backuppc
echo "Shutting down BackupPC..."
/etc/init.d/backuppc stop || die "Unable to shutdown backuppc, exiting..."
```

Change $1 to $@ in your die function.  It was my typo, that has since been corrected.

```
echo "Insert offsite backup drive if you have not done so."
echo

```

is more simply:

```
echo -e "Insert offsite backup drive if you have not done so.\n"
```

MrC

---

### Post by sacherjj on 2007-08-21
Ah...  I was reading resume (as in restart), not resumé.  That explains why all the searches just sounded like people being a smart a$$.  :)

Luckily, this is for folks that until I gave them some older computers loaded with BackupPC, they were running their businesses with ZERO backups.  It gave me stress, because I would be the first called when the crap hits the fan.

Locking down the write on the script and setting up the destination correctly in the script should only allow them to trash drives they put in the computer, not the actual backups themselves.

One thing I am going to try to add is a check for disk space used under /var/lib/backuppc and compare that to free space after format.  I assume I can grep the df command for the latter.  I need to find the command for getting size of a directory.

---

### Post by Mr. C. on 2007-08-21
```
df /mount/path
du -s /dir
```

MrC

---

### Post by s1ightcrazed on 2007-08-21
du -ks 'dirname'

You can also do du -h, which gives it in human readable format, but that doesn't work well in a script. Just output in Kbytes and compare with less than/greater than.

---

### Post by sacherjj on 2007-08-21
> **Mr. C. said:**
> Looks pretty good!

This will cause problems if the error occurs.  The script exits without un-mounting.

```
# Shutdown backuppc
echo "Shutting down BackupPC..."
/etc/init.d/backuppc stop || die "Unable to shutdown backuppc, exiting..."
```


Since I am trapping EXIT, won't the clean function run when the exit is called in die?

> **Mr. C. said:**
> 
is more simply:

```
echo -e "Insert offsite backup drive if you have not done so.\n"
```


Ahh..   -e.  I was trying to figure out why it was just taunting me by printing out my \n characters.  :)

I appreciate both of your help.  I'll be playing with this a little more tonight.

---

### Post by sacherjj on 2007-08-21
With the "$@" in the die, I can call it with multiple string arguments and these would be handled the same way as multiple echo statements, correct?

The reason I am asking is that I would like some dies to print two lines, just to be "better looking".  

Any disadvantage to using: ```
echo -e "$@"
``` in the die?

BTW - I quickly found out the echo --help or echo -h, doesn't really work.  :)  But the man page was helpful.

---

### Post by s1ightcrazed on 2007-08-21
for i in "$@"; do 
echo "$i"
done

this will loop through all of the arguments and print each with a seperate echo statement. You can call die() like"

die "Statement 1" "Statement 2"

and each statement will print on it's own line.

---

### Post by sacherjj on 2007-08-21
Since all I'm wanting is new lines, I think -e will be cleaner.

---

### Post by s1ightcrazed on 2007-08-21
Maybe I misunderstood. I thought you wanted to be able to call 'die' and have it print multiple lines if you pass it multiple statements. I don't see how '-e' is going to make a difference. In my test if I call die with:

die "Statement 1" "Statement 2"

I get:

Statement 1 Statement 2

This is with a die function of:

die() {
echo -e "$@"
}

I'm assuming that this is similar to the one that you are using (minus the exit).

---

### Post by sacherjj on 2007-08-21
I wasn't clear as well.  The reason is purely for formatting.  With the echo -e option, I will just put in some \n characters where I want breaks.  So I would send die "Statement 1\nStatement 2".

 I understand your code and thanks for posting it.  Always multiple ways to get to the end point.

---

### Post by Mr. C. on 2007-08-21
> **sacherjj said:**
> Since I am trapping EXIT, won't the clean function run when the exit is called in die?.

Yes, my oversight.

---

### Post by Mr. C. on 2007-08-21
> **s1ightcrazed said:**
> 
die "Statement 1" "Statement 2"

There really is no advantage to passing multiple arguments like this.  The goal is to to simply print a string.  The function shouldn't care how many strings are passed.  Instead, simple embed \n in the string and use a single echo -e.

$@ is all the arguments, so a single 

echo -e $@ is sufficient.

The die function would be called as:

die 'Line 1\nLine2\nLine3...\nLineN'

MrC

---

### Post by sacherjj on 2007-08-21
Not sure if there is a cleaner method, but I have added disk free space vs data size checking.  I added a check for BackupPC and restart if needed in the trap function.

```
#!/bin/bash
#
# This script was created to duplicate the /var/lib/backuppc directory
# used to store all the backup files for BackupPC.  This is used with
# a removable and hot swappable SATA drive bay to make backups that
# can be taken offsite.
#
# Created by Joe Sacher  joe@joesacher.com
#
# May be freely distributed and modified as needed, 
# as long as proper credit is given.
#

########################
# Start of user config #
########################

# Destination mount and device
mount_point="/mnt/offsite_backup"
dest_drive="/dev/sdc1"  # <- Probably only need to change this

# Source directory to copy to destination
source_path="/var/lib/backuppc"

# Source Config Directory
config_src="/etc/backuppc"

# Destination Config BackupPC
config_dest="etc_backup"

######################
# End of user config #
######################

# Should match the filename of this script
script_name="createoffsite"

# Backup name is 4 digit year and day of year.  Ex: 2007-232
backup_name=`date +%Y`-`date +%j`

function die()
{
	echo -e "$@"
	exit 1
}

function cleanUpMounting()
{
	echo "Cleaning up..."
	
	# Unmount drive, if mounted
	if mount | grep -q $dest_drive; then
		# Force the unmount, as the user will be ejecting the drive
		umount -f $dest_drive
	fi

	# remove mount point
	if [ -d "$mount_point" ]; then
		rmdir "$mount_point"
	fi

	# Restart BackupPC is needed
	if ! ps -el | grep -q BackupPC; then
		/etc/init.d/backuppc start
	fi
	
	# Remove trap so EXIT doesn't fire	
	trap - INT TERM EXIT

	# Must exit or will resume at place Signal occured
	echo "Exiting..."
	exit 1	
}

# Must run as root so that we can shutdown backuppc and mount drives 
[ $(whoami) == "root" ] || die "You need to run this script as root.\nUse 'sudo ./$script_name' then enter your password when prompted."

# Check if the mount point exists (it shouldn't)
[ ! -d "$mount_point" ] || die "Destination mount point: $mount_point already exists.\nPlease remove directory and rerun this $script_name."

# Verify that the destination drive isn't mounted and unmount if desired.
# mount returnsall drives mounted, if grep finds the destination drive it is mounted
if mount | grep -q $dest_drive; then
	echo "Destination drive ($dest_drive) is already mounted."
	read -p "Unmount and continue (y/n)?"
	[ "$REPLY" == "y" ] || die "Exiting..."
	
	umount $dest_drive
fi

echo -e "\nInsert offsite backup drive if you have not done so.\n"

# Verify that the user wants to wipe the destination drive
echo -e "The destination drive ($dest_drive) will be formatted.\nAll data on the drive will be lost!"
read -p "Continue (y/n)?"
[ "$REPLY" == "y" ] || die "Exiting..."

trap cleanUpMounting INT TERM EXIT

# Format destination drive (faster than delete, as this will have TONS 
# of files if is a used backup drive)
echo "Formatting destination drive: $dest_drive"
mke2fs -j $dest_drive || die "Error formatting destination drive, exiting..."

# Mount the drive
echo "Mounting destination drive to $mount_point"
mkdir $mount_point || die "Error creating mount point directory: $mount_point, exiting..."
mount -t ext3 $dest_drive $mount_point || die "Error mounting destination drive, exiting..."

# Shutdown backuppc
echo "Shutting down BackupPC..."
/etc/init.d/backuppc stop || die "Unable to shutdown backuppc, exiting..."

###
# Verify that destination drive has enough space
###

echo "Verifying destination has enough space for the copy operation..."

# Get single line containing size info for mount point
dfavail=`df $mount_point | grep $mount_point`
# split columns into array
dfavail=($dfavail)
# get the available size part
dfavail=${dfavail[3]}

# Get size of data to copy
# Main data - du style (This is extremely slow!)  
# Must use this or no size checking if /var/lib/backuppc is not a partition mount point.
#data_size=`du -s $source_path`
#data_size=($data_size)
#data_size=${data_size[0]}

# Main data - df style (Must have /var/lib/backuppc as mount point to partition)
data_size=`df $source_path | grep $source_path`
data_size=($data_size)
data_size=${data_size[2]}

total_size=$data_size

# Config data
data_size=`du -s $config_src`
data_size=($data_size)
data_size=${data_size[0]}
total_size=$(($total_size + $data_size))

echo "Data size: $total_size bytes  Free Space: $dfavail bytes"
# Compare sizes and exit if needed
[ $data_size -lt $dfavail ] || die "Target $dest_drive does not have enough free space to hold data being copied."

###
# End disk space verification
###

# Copy files preserving permissions, etc.
echo "Copying files..."
cd $source_path || die "Unable to change into source directory: $source_path, exiting..."
find . -depth -print0 | cpio --null --sparse -pvd $mount_point || die "Error copying main files..."

# Create directory for backingup BackupPC config_src
mkdir $mount_point/$config_dest || die "Unable to make directory on $dest_drive to backup config: $mount_point/$config_dest, exiting..."

# Backup config files
cd $config_src || die "Unable to change into config directory: $config_src, exiting..."
find . -depth -print0 | cpio --null --sparse -pvd $mount_point/$config_dest || die "Error copying config files..."

# Startup backuppc
echo "Completed backup, starting BackupPC..."
/etc/init.d/backuppc start || echo "BackupPC was not started correctly!"

# Create an empty file with Year and Day of Year for the backup
# this is just in case the label is removed from media.
touch $mount_point/$backup_name

# Unmount and cleanup
umount $dest_drive || die "Unable to unmount $dest_drive!"

# Remove mount point directory
if rmdir $mount_point; then
	echo "Process complete, you may now eject the offsite backup drive."
	# Label drive with 4 digit year - day of year
	echo "Label this drive: '$backup_name' ([Year]-[DayOfYear])"
else
	die "Unable to remove mount location: $mount_point!"
fi

# Reset trap so not called on exit
trap - INT TERM EXIT
exit 0
```

Wow is the du command slow for a real drive with 300 Gb of data on it.  I had been developing in Virtual PC on my laptop.  The du on my live BackupPC server is taking forever.  Are there any faster ways to do this?

I mount /var/lib/backuppc as a separate drive, so I can use df.  However, this won't work for just any backuppc installation.   All of mine are like that, so I changed the script to use it.  Much faster, almost instant size check.

---

### Post by Mr. C. on 2007-08-22
A directory has no notion of the size of its contents, so du must calculate the size of the contents recursively.  It is not fast.

I prefer a simple:

```
data_size=$(du -s $source_path | awk '{print $1}')
```

to the multistep sequence you've used.  You can do the same thing for df; just include a match pattern for awk:

```
data_size=$(/bin/df $source_path | tail -1 | awk '{print $3}') 
```

Be careful of your df.  df outputs the file system path, which is not necessarily the same path you pass as a parameter (try: df /tmp for example).

MrC

---

### Post by sacherjj on 2007-08-22
Thanks on the awk strings.  That looks much cleaner.

I understand the df issues, it will only work if the path is a mount point.  I've setup all the machines to have separate drives mounted at /var/lib/backuppc, so this should work for them.

The hot-swap SATA bay isn't working quite as well as I hoped with Ubuntu (might not with Windows either.)  Looks like I'll probably be going with a USB external drive instead.  So I'm sure I'll have to modify my script for that.

This has been a good learning experience.

---

