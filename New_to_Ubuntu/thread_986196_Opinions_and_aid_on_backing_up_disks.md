---
title: "Opinions and aid on backing up disks?"
date: 2008-11-18
forum: New to Ubuntu
---

### Post by tarahmarie on 2008-11-18
Hi, all:

I have two internal drives; I use the second drive as a crude backup for the first.

I'd like to streamline my backup process.  I've been simply copying my home drive over to the second drive (I have approximately 600GBs of data in my home folder, and my drives are 750GB each).

That's simplistic, unautomated, and irritatingly incomplete.  I'd like to copy some other stuff too, like my root bash profile, my PATH directories, my /etc/sources, etc, etc.  

I'd like some recommendations.  There's a few different programs out there, or I could just use cron and rsync (not that I actually KNOW how to use them yet, but I am aware that they exist and what they're for).

What do you all think?

---

### Post by Titan8990 on 2008-11-18
+1 for rysnc + cron. I use it to back up my entire system but you can have it only do specified files.

Here is an example of a rsync script (the one that I use):

```
#!/bin/sh

# %Y     year
# %m     month (01..12)
# %d     day of month (e.g, 01)
# %s     seconds since 1970-01-01 00:00:00 UTC

# Variable for the Program
BACKUPDIR=/
THEDATE=`date '+%Y%m%d-%s'`
LOGDIR=/var/log/backup
EXCLUDEFILE=/scripts/exclude
LOGFILE=/var/log/backup/rsync-$THEDATE.log
GZFILE=/var/log/backup/rsync-$THEDATE.gz
DESTINATION=/media/backup/backup0
LAST=/media/backup/backup5
MNTPOINT=/media/backup/
BACKUPD=/dev/sda1

#Check to make sure that our backup drive is mounted - To be included later


#If the log directory does not exist then create it

if [ ! -d $LOGDIR ]; then
    mkdir -p $LOGDIR
fi

#If the destination directory does not exist then create it

if [ ! -d $DESTINATION ]; then
        mkdir -p $DESTINATION
fi

#Rotate the backups

rm -rf $LAST
mv /media/backup/backup4 $LAST
mv /media/backup/backup3 /media/backup/backup4
mv /media/backup/backup2 /media/backup/backup3
mv /media/backup/backup1 /media/backup/backup2
cp -al $DESTINATION /media/backup/backup1

#Now run rsync to backup the filesystem

rsync -altvr --delete --delete-excluded --exclude-from=$EXCLUDEFILE --log-file=$LOGFILE $BACKUPDIR $DESTINATION

# gunzip the logfile
gzip -c $LOGFILE > $GZFILE

# delete the original, uncompressed logfile
rm $LOGFILE
```

---

### Post by rampageoberon on 2008-11-18
I use "mirrordir" to copy some of the files i'd like to backup. Ideally you'd want to backup your key configurations so xorg.conf etc.

I just tend to do my home folder only and the scripts i have written

---

### Post by beercz on 2008-11-18
> **tarahmarie said:**
> Hi, all:

I have two internal drives; I use the second drive as a crude backup for the first.

I'd like to streamline my backup process.  I've been simply copying my home drive over to the second drive (I have approximately 600GBs of data in my home folder, and my drives are 750GB each).

That's simplistic, unautomated, and irritatingly incomplete.  I'd like to copy some other stuff too, like my root bash profile, my PATH directories, my /etc/sources, etc, etc.  

I'd like some recommendations.  There's a few different programs out there, or I could just use cron and rsync (not that I actually KNOW how to use them yet, but I am aware that they exist and what they're for).

What do you all think?

I think rsync is the way to go

The basic command structure is:

rsync options source destination

You will have to do it both ways of course - from your first to your second drive and then from your second to your first drive.  You will then have 2 copies of the data on the two drives.

Once that's done, assuming that the 2nd drive is to be your backup, you will only need to run rsync everytime you wish to back up your first drive to your second.

Try [http://rsnapshot.org](http://rsnapshot.org) which will do automatic backups - once configured you can then run rsnapshot at regular intervals using cron.

Start with > man rsync to get yourself familiar with the command.  It really isn't that difficult once you get to know it.

Post back with specific questions if necessary.

---

### Post by phidia on 2008-11-18
If you're interested in cloning your install you could check out [clonezilla]("http://www.clonezilla.org/"). There has been a release release too.

---

### Post by tarahmarie on 2008-11-18
Ok, it sounds like cron and rsync is the way to go.  Can anyone point me to the best tutorial on how to write the scripts for it?

---

### Post by Titan8990 on 2008-11-18
You could take mine poster earlier and alter the variables to fit your needs. In your case, your exclude file may include the majority of the fileysystem.

---

### Post by tarahmarie on 2008-11-18
Well, I'm kinda nervous about using rsync--usually in Linux, as far as I've seen, a "powerful" command == "a command which can really %$#@ up your system if you use it wrong."

How could I test this script without actually USING it?

---

### Post by jonofan on 2008-11-18
If you have two 750GB disks why not just setup a RAID?

---

### Post by Titan8990 on 2008-11-18
IMO if you don't have a discrete RAID controller, you should not be implementing a RAID.

On top of that, **RAID is not a substitute for regular backups**


> 
How could I test this script without actually USING it?


Only way I can think of is by using a virtual machine. As long as you don't reverse the source in destination, you should be fine.

---

### Post by jonofan on 2008-11-18
_**From Wikipedia:**_
RAID 1 (mirrored disks) could be described as a backup solution, using two (possibly more) disks that each store the same data so that data is not lost as long as one disk survives. Total capacity of the array is just the capacity of a single disk. The failure of one drive, in the event of a hardware or software malfunction, does not increase the chance of a failure nor decrease the reliability of the remaining drives (second, third, etc).

I would think a RAID would be more suitable in this situation as disks are of equal size. This would save the time taken for the cron + rsync script to be run.

---

### Post by tarahmarie on 2008-11-18
Geez--I have to set up a virtual machine to test rsync?  

Ok, scratch the rsync option.  Anyone know anything about Clonezilla?  I read about it in Lifehacker; anyone tried it?

---

### Post by tarahmarie on 2008-11-24
So, if I wanted to use rsync to back up one full hard drive to another, how would it work?  I've looked at online tutorials, but I'm not confident enough yet in bash to set it up.  Does it look like this?

To back up everything on my primary hard drive to the main partition on my secondary internal drive:

rsync=/ /media/secondDrive

Is that what it should look like?

---

### Post by scribbles on 2008-11-24
Clonezilla definitely looks like the way to go. That way you have a full image ready to put back on a new drive in case of failure. You won't have to resetup all the programs you've spent so much time getting just right...

I also found [Remastersys]("http://www.remastersys.klikit-linux.com/") recently, it looks like it has some interesting features too...

---

### Post by Titan8990 on 2008-11-24
That is close. You are missing arguments that will make it work properly.


First, we start with initial command:

rsync


Then we need to tell rsync how to operate:


rsync -avlt

Lets look at what these do:

a - archive

v - verbose (display information about what rsync is doing)

l - preserve symbolic links

t - preserve time


Now we can add the directory we need to rsync. For the whole filesystem it will be /:

rsync -rvlt / 


Last thing is to add the destination directory:


rsync -rvlt / /media/secondDrive


The above is full command you are looking for.

---

### Post by tarahmarie on 2008-11-24
And to run it at a specified time, I'm informed that I can use cron through the kcron frontend in System Settings on KDE4...there seems to be a problem, though.  I can't sign into administrative privileges to use the System Cron option.  Do I even need to do so?  Can I rsync without administrative privileges if I'm backing up /?

---

### Post by Titan8990 on 2008-11-24
No, you need administrative privileges. Here is another section I have wrote about setting up rsync for the script that I posted earlier in the thread.

The cron job must be set as root. This means you can not sudo you will need to change users with the command: sudo -i.

The create a cronjob you would use the following command:

```
EDITOR=nano && crontab -e
```

You can use whatever editor you prefer. The code above uses nano which should be more than sufficient.

The syntax of crontabs:

minute (0-59), hour (0-23, 0 = midnight), day (1-31), month (1-12), weekday (0-6, 0 = Sunday), command

It will look like this commented at the top of your crontab file:

```
m  h  dom  mon  dow  command
```

If we want to run something daily then we insert wild cards for dom, mon, and dow. Example:
```

30 14 * * * COMMAND
```

Here is what it looks like on my computer:

```
00 23 * * * /scripts/rsync.sh >/dev/null 2>&1 
```

That is all there is to it. The above crontab will execute our backup at 11pm every nite. The ">/dev/null 2>&1" prevents cron from mailing you about the results of the cron job. We do not need this because our cron job saves a log anyways. I recommend always dumping the mail.


Feel free to post both your script and cron screen. I will let you know if there are any errors.

---

### Post by Titan8990 on 2008-11-24
Sorry for double post. Just wanted to say, cron is much simpler than it looks. After you have created your first one, it will be a breeze after that. 

Also, don't forget to add a shebang to the top of your scripts:


#!/bin/sh

---

### Post by tarahmarie on 2008-11-24
Ok, here is my rsync.sh

#!/bin/sh
rsync -rvlt / /media/secondDrive

And my crontab:

# m h  dom mon dow   command
00 03 * * *
/home/tarahmarie/Documents/Scripts/rsync.sh
>/dev/null
2>&1

Is that right?

---

### Post by tarahmarie on 2008-11-24
Also, I got this error when trying to save that crontab:

crontab: installing new crontab
"/tmp/crontab.Wn9Duq/crontab":2: bad minute
errors in crontab file, can't install.
Do you want to retry the same edit?

---

### Post by Titan8990 on 2008-11-24
Take a screenshot of your editing of crontabs.


To take a screenshot of a single window in Ubuntu (and all other OS I have used), hit ATL+PrtScn.

---

