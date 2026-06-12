---
title: "Making room and hard drive problems"
date: 2012-01-03
forum: New to Ubuntu
---

### Post by DGINSD on 2012-01-03
In system monitor its showing my / partition is 99% full, I had installed both the KDE and XFCE desktops to try 'em out, but after seeing this I figured I better remove hem to make more room. I opened up Synaptic Package Manager selected them both and all the ones that came with them to "Completely Remove" I also completely removed a lot of games I'll never use, then re booted. When I checked system monitor again I still was 99% full as if nothing had been removed. So I pulled up disk usage analyzer and found some strange things, /log was taking up 9+ Gig, my Windoz XP partition was mounted at /media and taking up 4+ gig (fresh non updated install). Also in System Monitor my Windoz XP partition is shown as "blkfuse" instead or "NTFS" (from my recollection), I unmounted and now can't get it to remount) 

So here's my questions; how can I safely determine and remove the log files taking up all that space? 

Why after removing all that stuff did I get no more free space? 

Why is my Windoz partition taking up room on my Ubuntu root partition? 

Shouldn't my windoz partition mount at "/mount" as "NTFS" and not register as taking up space on my Ubuntu partition and if so how do I fix this?

---

### Post by oldfred on 2012-01-03
I think all the Windows and maybe some others use the fuseblk system.
[http://en.wikipedia.org/wiki/Filesystem_in_Userspace](http://en.wikipedia.org/wiki/Filesystem_in_Userspace)

Just deleting usually does not free up space as it is just moved to trash.

Housecleaning:

HOWTO: Recover Lost Disk Space - drs305
[http://ubuntuforums.org/showthread.php?t=1122670](http://ubuntuforums.org/showthread.php?t=1122670)
HOWTO: Cleaning up all those unnecessary junk files...
[http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)
    Caution deborphan will delete anything you manually installed. See comment:
Better to use Synaptic to select the ones you no longer want. Also you get notified about dependencies to be removed and can reconsider, if need be.
[http://lifehacker.com/5817282/what-kind-of-maintenance-do-i-need-to-do-on-my-linux-pc](http://lifehacker.com/5817282/what-kind-of-maintenance-do-i-need-to-do-on-my-linux-pc)

HouseKeeping:
sudo apt-get update #resync package index
sudo apt-get upgrade #newest versions of all packages, update must be run first
sudo apt-get autoremove  #removes depenancies no longer needed
# removes .deb
sudo apt-get autoclean   # only removes files that cannot be downloaded anymore (obsolete)
Sometimes this does more?
sudo apt-get dist-upgrade  #updates dependancies

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

# empty trash
# remove log files if no issues
cd /var/log
sudo rm -f messages.*
sudo rm -v /var/log/*.gz

Check for files with tilde
find $HOME -type f -name "*~" -print
This will delete them, but then you have no hidden backups.
find $HOME -type f -name "*~" -print -exec rm {} \; 

#check for large files:
sudo du -h --max-depth=1 / | grep '[0-9]G\>'   # folders larger than 1GB
sudo find / -name '*' -size +1G    # files larger than 1GB
find . -maxdepth 1 -type d ! -name . -exec du -sh '{}' \; | sort -h
dpkg-query -Wf '${Installed-Size}\t${Package}\n' | sort -n
gksudo nautilus /root/.local/share/Trash/files  # Be sure to enable viewing of hidden files.

Trash
Here is where these files normally reside.

    * ~/.local/share/Trash User's Trash (hardy and later)
    * ~/.Trash User's Trash (pre-hardy)
    * /root/.local/share/Trash System Trash (hardy and later)
    * /root/.Trash System Trash (pre-hardy):
    * /.local/share/.Trash-1000 NTFS/FAT32/etc: Trash deleted in these partitions is placed in a Trash bin named in accordance with the user deleting the file, e.g. -1000, 1002, -0, etc

rm -rf ~/.local/share/Trash/*
use -ri options, so that it prompts for each file deletion to be safer.

If you get permission problems try to slip a sudo in front of the commands, but be sure that the path is correct as rm can be dangerous command.

---

### Post by DGINSD on 2012-01-03
Excelent I'll give it a whirl when I get back home. There's got to be a way to automate all that so your disc doesn't fill up that fast.

What about my windoz partition counting against  space on my /, and does my /home (seprate partition) also get counted as used space towards /?

---

### Post by oldfred on 2012-01-03
Different partitions do not really count as space against your root. Some tools  are just showing totals, so you have to check with different apps and know which are showing totals and which are showing just a partition.

I use this to know how full things really are:
```

fred@fred-LT-A105:~$ df -Th | sort
/dev/sda1  fuseblk     55G   43G   12G  79% /mnt/cdrive
/dev/sda2  fuseblk     30G   24G  6.0G  80% /mnt/shared
/dev/sda5     ext4     15G  9.7G  4.1G  71% /
/dev/sda7     ext3     48G   20G   26G  43% /mnt/data
/dev/sdb1     vfat    359M  336M   23M  94% /media/C0CC-4E19
/dev/sdb2     ext2    1.6G  747M  714M  52% /media/New Volume
Filesystem    Type    Size  Used Avail Use% Mounted on
none      devtmpfs    740M  280K  740M   1% /dev
none         tmpfs    747M     0  747M   0% /var/lock
none         tmpfs    747M  2.6M  744M   1% /dev/shm
none         tmpfs    747M  348K  747M   1% /var/run
 
```

---

### Post by DGINSD on 2012-01-03
That output looks a might confusing, but then again I don't know the set up of your machine.

Is there any benifit to having a seprate home partition, or even further dividing things up? I even remember reading a post about having a seprate wine partition but I cant remember where it was, and I've kind of thinking of going windozs-less now that I've discovered wine but I still need to test a few things. I''ve never gotten DVD backing up to work very well in ubuntu so if I could get my windoz programs to work in wine I might not need windoz any more.

---

### Post by oldfred on 2012-01-03
My understanding is that .wine is more difficult to move. But if not a more advanced user having just a separate /home is fine. The advantage of a separte /home is that then you can do clean installs and reuse the same /home. You should still be backing up /home anyway, but it makes the install easier. But, I had just root, swap & a shared NTFS with XP on another drive for at least two years.

The above is from my portable which has XP, a NTFS shared, an ext3 data partition and shows the mount of a flash drive. I have my portable set up with shared & data as partitions as that is how my desktop is set up with multiple drives. I want to be able to copy data to laptop when I travel and have all the same configurations (except UUIDs).

Only if installing multiple systems or other advanced set ups would the separate shared NTFS or ext3 data make some sense.

---

### Post by DGINSD on 2012-01-04
> **oldfred said:**
> Different partitions do not really count as space against your root. Some tools  are just showing totals, so you have to check with different apps and know which are showing totals and which are showing just a partition.

I use this to know how full things really are:
```

fred@fred-LT-A105:~$ df -Th | sort
/dev/sda1  fuseblk     55G   43G   12G  79% /mnt/cdrive
/dev/sda2  fuseblk     30G   24G  6.0G  80% /mnt/shared
/dev/sda5     ext4     15G  9.7G  4.1G  71% /
/dev/sda7     ext3     48G   20G   26G  43% /mnt/data
/dev/sdb1     vfat    359M  336M   23M  94% /media/C0CC-4E19
/dev/sdb2     ext2    1.6G  747M  714M  52% /media/New Volume
Filesystem    Type    Size  Used Avail Use% Mounted on
none      devtmpfs    740M  280K  740M   1% /dev
none         tmpfs    747M     0  747M   0% /var/lock
none         tmpfs    747M  2.6M  744M   1% /dev/shm
none         tmpfs    747M  348K  747M   1% /var/run
 
```

I had two 4 gig log files got rid of those and things look more normal. I tried to figure out what was causing the log o fill up but every time I tried to ope up the files my computer bogged and froze up and I had to force a power down. 

About Other partitions counting against root in some graphical programs, that's kinda a big bug overlooked by the developers and very confusing, also I was still getting "no room warnings" but if you subtracted what home and media was adding there was still plenty of space.

---

### Post by oldfred on 2012-01-04
A 4GB file becomes difficult to open. Even if the app will load it, it will use swap and be very slow.

Did you try less or more as they do not open entire file. 
man less
man more

If logs are filling up that fast some process is running and having major issues. I would think you would quickly get a new log file that is smaller.

---

### Post by DGINSD on 2012-01-04
> **oldfred said:**
> A 4GB file becomes difficult to open. Even if the app will load it, it will use swap and be very slow.

Did you try less or more as they do not open entire file. 
man less
man more

If logs are filling up that fast some process is running and having major issues. I would think you would quickly get a new log file that is smaller.

I forgot about the less and more commands still kinda new to the command line so I didn't even think of that. I cleared the log files with a command listed in one of the tutorials you linked to, no new listings have generated.

Is there a good way to automate cleaning out these old log files so my drive doesn't get eaten up with redundant entries, what I say of the 4gig log was the same entry over and over again?

---

### Post by wildmanne39 on 2012-01-04
Hi DGINSD, it may have been the issue you were having with your wireless connection that filled up your log, did you get a good look at it?
Thanks

---

### Post by oldfred on 2012-01-05
As with any rm command make sure you are in the correct location and run the command exactly. rm can be very dangerous especially with a sudo in front of it.

# remove log files if no issues
cd /var/log
# show files
 ls -l
# force delete of messages
sudo rm -f messages.*
# Deletes all .gz (older)
sudo rm -v /var/log/*.gz

-f is force which means it will do it, -v is verbose so you can see what is is doing. May be safer to use -i or -I as then it asks on each file or three files - see man rm.

---

### Post by DGINSD on 2012-01-06
> **wildmanne39 said:**
> Hi DGINSD, it may have been the issue you were having with your wireless connection that filled up your log, did you get a good look at it?
Thanks

I did and the one in the kernel log and the system log both of which were 4 gig + have a few random entries but there was one that was over and over, I tried copying it to paste it here but I had to force a shut down, so I lost it. I keep hoping another log will generate to I can post it and hopefully get it fixed.

---

### Post by wildmanne39 on 2012-01-06
Hi, hopefully it is already fixed and there will be no more errors.
Thanks

---

### Post by DGINSD on 2012-01-06
> Hi, hopefully it is already fixed and there will be no more errors.
Thanks
_________________

Meh, I'm not that lucky the log files seem to be filling up again some related to wifi and network connections, I'll post in my thread about the wifi connection. Should these log files get full all the time or is that a sign something is wrong with my set up. Can I automate clearing out these log files, so they don't kep filling up my hard disk?

---

### Post by wildmanne39 on 2012-01-07
Hi, it is normal to have a lot of information in log files, it is not good if you are getting serious errors and your system is not working properly, however everyone gets some errors that are not serious and are not worth worring about in my opinion but I am not an expert so I will let someone with more experience with log files answer your question on how best to deal with them because of your space issues.
Thanks

---

