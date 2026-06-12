---
title: "Backup!!!!!"
date: 2011-08-18
forum: Outdated Tutorials &amp; Tips
---

### Post by dbol on 2011-08-18
Hello All,

I have attempted to write my first complex (to me) backup script. I am offering it to any and all who may find it useful but would like to refine it as well. I'm using it to backup my *nix server to a USB Raid5. The script is actually comprised of a daily and a weekly script. Please provide any and all comments, corrections etc. Thanks in advance.

```

```
#!/bin/sh
## DAILY BACKUP
##
Source1=/Volumes/Data/Aperture_Share
Source2=/Volumes/Data/iTunes_Share
Source3=/Volumes/Data/Public
Source4=/Users/admin
Destination=/Volumes/Backup/MediaServer/
Excludes=/Volumes/Backup/MediaServer/excludes.txt
Logfile=/Volumes/Backup/MediaServer/daily_logs/dailylog.txt
Logfilegzip=/Volumes/Backup/MediaServer/daily_logs/dailylog.txt.gz
##
diskutil mount /dev/disk3s2
echo "#######################################" >>$Logfile 
echo "***************************************" >>$Logfile
echo "~~~~~~~~Starting Daily Backup~~~~~~~~~~" >>$Logfile
date >>$Logfile
/usr/local/bin/rsync -avzxpP --stats --exclude-from=$Excludes $Source1 $Source2 $Source3 $Source4 $Destination/current/ >>$Logfile
date >>$Logfile
echo "~~~~~~~~Finished Daily Backup~~~~~~~~~~" >>$Logfile
echo "***************************************" >>$Logfile
echo "#######################################" >>$Logfile
##
gzip $Logfile
cp $Logfilegzip /Volumes/Backup/MediaServer/daily_logs/"`date +%m%d%y`_dailylog.txt.gz"
uuencode $Logfilegzip $Logfilegzip | mailx -s "Daily MediaServer Backup" [email]user@gmail.com[/email]
rm $Logfilegzip
sleep 20
diskutil umount /dev/disk3s2
##
```

```
```

```
#!/bin/sh
## WEEKLY BACKUP
##
Source1=/Volumes/Data/Aperture_Share
Source2=/Volumes/Data/iTunes_Share
Source3=/Volumes/Data/Public
Source4=/Users/admin
Destination=/Volumes/Backup/MediaServer/
Excludes=/Volumes/Backup/MediaServer/excludes.txt
Logfile=/Volumes/Backup/MediaServer/weekly_logs/weeklylog.txt
Logfilegzip=/Volumes/Backup/MediaServer/weekly_logs/weeklylog.txt.gz
##
diskutil mount /dev/disk3s2
echo "#######################################" >>$Logfile
echo "***************************************" >>$Logfile
echo "~~~~~~~Starting Weekly Backup~~~~~~~~~~" >>$Logfile
date >>$Logfile
/usr/local/bin/rsync -avzxpP --stats --exclude-from=$Excludes $Source1 $Source2 $Source3 $Source4 $Destination/current/ >>$Logfile  
rm -rf $Destination/snapshot.3   
mv $Destination/snapshot.2 $Destination/snapshot.3  
mv $Destination/snapshot.1 $Destination/snapshot.2 
mv $Destination/snapshot.0 $Destination/snapshot.1 
cd $Destination/current
find . -print | cpio -dumpvl $Destination/snapshot.0
/usr/local/bin/rsync -avzxpP --stats --delete --exclude-from=$Excludes $Source1 $Source2 $Source3 $Source4 $Destination/current/ >>$Logfile  
date >>$Logfile
echo "~~~~~~~~Finished Weekly Backup~~~~~~~~~" >>$Logfile
echo "***************************************" >>$Logfile
echo "#######################################" >>$Logfile
##
gzip $Logfile
cp $Logfilegzip /Volumes/Backup/MediaServer/weekly_logs/"`date +%m%d%y`_weeklylog.txt.gz"
uuencode $Logfilegzip $Logfilegzip | mailx -s "Weekly MediaServer Backup" [email]user@gmail.com[/email]
rm $Logfilegzip
sleep 20
diskutil umount /dev/disk3s2
##
```

```

---

