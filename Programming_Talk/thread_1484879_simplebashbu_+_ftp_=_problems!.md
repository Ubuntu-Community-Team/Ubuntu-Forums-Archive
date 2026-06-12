---
title: "simplebashbu + ftp = problems!"
date: 2010-05-16
forum: Programming Talk
---

### Post by MaddMatt on 2010-05-16
Hi All Bash coders!

I found a neat script called "simplebashbu" (bu for back-up) hosted here: [http://simplebashbu.sourceforge.net/](http://simplebashbu.sourceforge.net/)

The script works fine, and I have it regularly backing up important directories to our server at 12 hour intervals. The trick is that I want to upload the newly gzipped archive to an off-site FTP server. So, I added this code to the bottom of the script, right after the gzip finishes:

```


# Upload to FTP server:
	echo "starting FTP routine..."
	echo "$UFTP  Host: $FTPHOST User: $FTPUSER"
      if test $UFTP -eq 1
	then
	echo "Connecting..."
	cd $TODAYSBACKUPDIR
	pwd
	ftp -n -v $FTPHOST<<-ENDFTP
	user $FTPUSER $FTPPASS
	cd $HOSTFTPDIR
	bin
	put $OUTFILEGZ
	bye
	ENDFTP
     else
	echo "FTP upload disabled: local copy only."
     fi
    done
fi


```

Naturally UFTP=0 for disabled, and 1 for enabled, and the host, user, and password are stored at the top of the script.

Anyway, I've tested this code on its own and it runs fine- and furthermore it outputs the FTP progress to the shell, so I can debug. But, nested in the simplebashbu script, not only does the code not execute, but the echo statements I put in to tell me if something has gone wrong also don't show up on in the log or shell. What gives? I've been banging my head on this one off and on for a few days now, and can't figure it out. The code is located before changing standard output back, so it should show up in the log. Any ideas?

Here's the code in its entirety:

```

#!/bin/bash
#
# COPYRIGHT:
# (c) 2001 Chris Arrowood (GNU LGPL V2.1)
# Edited in 2010 by MR
# You may view the full copyright text at:
# http://www.opensource.org/licenses/lgpl-license.html
#
# DESCRIPTION:
# A simple BASH script to do nightly backups to tarballs
# on a hard drive (not to tape)  Ideal for home linux users
# to easily backup thier system, provided they have an extra 
# hard drive.
#


###############################################
#              User Variables                 #
###############################################
#
# Modify these variables to suit your needs
#
# Which day of the week do we want to do full backups? 0=Sunday
# This version is intended to be used by cron. Don't change:
  LEVEL0DAY=0
# Where to create the backups; It should already exist
  BACKUP_DIR=/backupdir
# Filesystems to backup separated by spaces and the entire string in double quotes; each must start with /
  FILESYSTEMS="/somedir/"
# Static filename if only backing up one directory:
  STATICFILENAME="somefile"
# Should we email results? Also should we email critical errors?  0=false, 1=true 
  EMAIL=0
# EMAIL address to send results to
  EMAILADDRESS=*******
# Email Subject
  EMAILSUBJECT="Database $HOSTNAME Backup Report"
# Only keep last weeks level0 backup (0) or keep all lvl 0 backups (1).  Keeping all data may take a lot of space!
  KEEPALL=0
# Do we wnat to compress the backup file using gzip? 0=false, 1=true
  COMPRESS=1
# Should we compress the log file when we are done?  0=false, 1=true
  COMPRESSLOG=0
# If we are compressing, what level do we use?
  COMPRESSLEVEL=6
# Determines whether we see all output to screen. It will still go to log regardless of this value.   0=false, 1=true 
  QUIET=0
# Would you like to get detailed information from tar and gzip? 0=false, 1=true   
  VERBOSE=1
# Upload to FTP 0 is no, 1 is yes?
  UFTP=1
# FTP Hostname:
  FTPHOST="10.0.0.1"
# FTP Username:
  FTPUSER="user"
# FTP Password:
  FTPPASS="pass"
# Remote target FTP directory
  HOSTFTPDIR="\"/Upload-Dir\""
# DO NOT EDIT BELOW THIS LINE
#--------------------------------------------------------



###############################################
#     Application Variables -  DO NOT EDIT    #
###############################################
# Day of the week;
  DAYOFWEEK=`date +"%w"`
# Folder for all daily backups
  DAILYBACKUPDIR=$BACKUP_DIR/DAILY
# Name of directory to create for current backup  
  TODAYSBACKUPDIR=$DAILYBACKUPDIR/$DAYOFWEEK
# directory to store last weeks data
  ARCHIVEDDATADIR=$BACKUP_DIR/ARCHIVED_BACKUPS
# Location of a file to hold the date stamp of last level 0 backup
  L0DATESTAMP=$BACKUP_DIR/.level0_datestamp
# Do I really need to explain this one ;-)
  NOW=`date`
# Log dir
  LOGDIR=$BACKUP_DIR/LOGS
# Svript name
  SCRIPTNAME="Simple Bash Backup Script"
# Version
  VERSION="0.02 - May 2010 edits"
# Copyright
  COPYRIGHT="(c) 2001 Chris Arrowood (GNU GPL V.2)"
# If user choose verbose, set the verbose command. Otherwise leave empty
if [ $VERBOSE -eq 1 ]
  then 
  VERBOSECOMMAND="--verbose"
fi
# Logfile
  LOGFILE=$LOGDIR/`date +"%Y-%m-%d_%H%M"`.log


######## Do some error checking #########
# Does backup dir exist?
if [ ! -d $BACKUP_DIR ]
  then
    #Send Email and Exit
    if [ $EMAIL -eq 1 ]
      then
      echo "The specified backup directory $BACKUP_DIR does not exist. Operation canceled." | mail -s "$EMAILSUBJECT" $EMAILADDRESS
    fi
    echo "The specified backup directory $BACKUP_DIR does not exist. Operation canceled."
    exit 1
fi
# Does the daily backup dir exist? If not, create it.
if [ ! -d $DAILYBACKUPDIR ]
  then
    mkdir $DAILYBACKUPDIR
fi
 
# Does the daily backup dir exist? If not, create it.
if [ ! -d $LOGDIR ]
  then
    mkdir $LOGDIR
fi



####### Redirect Output to a logfile and screen - Couldnt get tee to work
exec 3>&1                         # create pipe (copy of stdout)
exec 2>&1                         # uncomment if you want stderr too
exec 1>$LOGFILE                   # direct stdout to file
if [ $QUIET -eq 0 ] 
  then tail -f $LOGFILE >&3 &     # run tail in bg
fi



######## DO SOME PRINTING ###############
echo " "
echo "#######################################################################"
echo "$SCRIPTNAME "
echo "Version $VERSION" 
echo "$COPYRIGHT"
echo " "
echo "Host: $HOSTNAME "
echo "Start Time: $NOW"
echo "#######################################################################"
echo " "
echo " "
echo " "





######## Run Backup #########
#if day is LEVEL0DAY do full backup
#if test $DAYOFWEEK -eq $LEVEL0DAY
#run by cron; DOW scheduling not necessary:
if test $LEVEL0DAY -eq 0
  then
    LEVEL=0
    #we need to archive the last full backup to the weekold dir
    #make sure the week-old dir exists
    if test -d $ARCHIVEDDATADIR
      then 
        #remove old data unless KEEPALL is set to 1
        if test $KEEPALL -eq 0
          then rm -Rf $ARCHIVEDDATADIR/*
        fi
      else
        #the week-old data dir didnt exist; create it
	mkdir $ARCHIVEDDATADIR
        chmod 700 $ARCHIVEDDATADIR
    fi
    #move the last full backup to the weekold dir
    mv -f $TODAYSBACKUPDIR/* $ARCHIVEDDATADIR > /dev/null 2>&1
    #remove all daily backups since they are simply incrementals on the bu we just archived
    rm -Rf $DAILYBACKUPDIR/*
    #make todays dir since we just blew it away
    mkdir $TODAYSBACKUPDIR
    #do FULL backup for each filesystem specified 
    for BACKUPFILES in $FILESYSTEMS
    do
      #Create the filename; replace / with .
      #WITHOUTSLASHES=`echo $BACKUPFILES | tr "/" "."`
      #WITHOUTLEADINGDOT=`echo $WITHOUTSLASHES | cut -b2-`
      OUTFILENAME=$STATICFILENAME.`date +"%Y-%m-%d_%H%M"`.tar
      OUTFILE=$TODAYSBACKUPDIR/$OUTFILENAME
      STARTTIME=`date`
      echo " "
      echo " "
      echo "#######################################################################"
      echo "$STARTTIME: Creating a level $LEVEL backup of $BACKUPFILES to $OUTFILE" 
      echo "#######################################################################"
      tar --create $VERBOSECOMMAND \
        --file $OUTFILE \
        --label "Level-$LEVEL Backup ${NOW}" \
        $BACKUPFILES 
      if test $COMPRESS -eq 1
        then
        #gzip it
	OUTFILEGZ=$OUTFLIE.gz        
	echo "Compressing to $OUTFILEGZ"   
        gzip -$COMPRESSLEVEL $VERBOSECOMMAND $OUTFILE
        rm -f $OUTFILE
      fi
    done
    # Does the timestamp file exist? If not, create it.
    if [ ! -w $L0DATESTAMP ]
      then
       touch $L0DATESTAMP
    fi    
    #record full backup timestamp
    echo $NOW > $L0DATESTAMP
  else
    #we should do an incremental backup
    LEVEL=1
    # Does todays backup dir exist? If not, create it.
    if [ ! -d $TODAYSBACKUPDIR ]
      then
        mkdir $TODAYSBACKUPDIR
    fi    
    # Does the timestamp file exist? If not, create it.
    if [ ! -w $L0DATESTAMP ]
      then
       touch $L0DATESTAMP
       echo "1969-12-31" > $L0DATESTAMP
    fi
    #get date of last full backup
    LAST=`cat $L0DATESTAMP`
    #Do a level 1 Backup for each filesystem specified
    for BACKUPFILES in $FILESYSTEMS
    do
      #Create the filename; replace / with .
      #WITHOUTSLASHES=`echo $BACKUPFILES | tr "/" "."`
      #WITHOUTLEADINGDOT=`echo $WITHOUTSLASHES | cut -b2-`
      #OUTFILENAME=$WITHOUTLEADINGDOT.`date +"%Y-%m-%d_%H%M"`.tar
      #Static output filename:
      OUTFILENAME=$STATICFILENAME.`date +"%Y-%m-%d_%H%M"`.tar
      OUTFILE=$TODAYSBACKUPDIR/$OUTFILENAME
      STARTTIME=`date`
      echo " "
      echo " "
      echo "#######################################################################"
      echo "$STARTTIME: Creating a level $LEVEL backup of $BACKUPFILES to $OUTFILE" 
      echo "#######################################################################"
      tar --create $VERBOSECOMMAND \
        --file $OUTFILE \
        --after-date "$LAST" \
        --label "Level-$LEVEL Backup from $LAST to $NOW" \
        $BACKUPFILES 
      if test $COMPRESS -eq 1
        then
        #gzip it
	OUTFILEGZ="$OUTFILENAME.gz"        
	echo "Compressing to $OUTFILEGZ"        
	gzip -$COMPRESSLEVEL $VERBOSECOMMAND $OUTFILE
	rm -f $OUTFILE
      fi
      
# Upload to FTP server:
	echo "starting FTP routine..."
	echo "$UFTP  Host: $FTPHOST User: $FTPUSER"
      if test $UFTP -eq 1
	then
	echo "Connecting..."
	cd $TODAYSBACKUPDIR
	pwd
	ftp -n -v $FTPHOST<<-ENDFTP
	user $FTPUSER $FTPPASS
	cd $HOSTFTPDIR
	bin
	put $OUTFILEGZ
	bye
	ENDFTP
     else
	echo "FTP upload disabled: local copy only."
     fi
    done
fi




SCRIPTFINISHTIME=`date`
echo " "
echo " "
echo " "
echo " "
echo "#######################################################################"
echo "Finish Time: $SCRIPTFINISHTIME"
echo " "
echo "  NOTE: Always examine the output of this script carefully for errors."
echo "        Also, be sure to verify your backups and your ability to "
echo "        retsore from them. "
echo "#######################################################################"



#email notification

if [ $EMAIL -eq 1 ]
  then cat $LOGFILE | mail -s "$EMAILSUBJECT" $EMAILADDRESS
fi


#Fix stdout and stderr to go to console instead of og file since we are 
#about to compress the log file
exec 1>&3                   
exec 2>&3


#compress log file?
if test $COMPRESSLOG -eq 1
  then
  #gzip it
  gzip -$COMPRESSLEVEL $LOGFILE  > /dev/null 2>&1
  rm -f $LOGFILE  > /dev/null 2>&1
fi




exit 0

```

Thanks

---

### Post by hannaman on 2010-05-16
I am not sure about bash, but in ksh, the whitespace would cause me problems.  Try removing the whitespace like this.
```
 if test $UFTP -eq 1
	then
	echo "Connecting..."
	cd $TODAYSBACKUPDIR
	pwd
ftp -n -v $FTPHOST<<-ENDFTP
user $FTPUSER $FTPPASS
cd $HOSTFTPDIR
bin
put $OUTFILEGZ
bye
ENDFTP
     else
	echo "FTP upload disabled: local copy only."
     fi

```

---

### Post by MaddMatt on 2010-05-16
> **hannaman said:**
> I am not sure about bash, but in ksh, the whitespace would cause me problems.  Try removing the whitespace 

Thanks hannaman. Whitespace has not been an issue in any previous bash scripting I've done, but I removed the whitespace and got no improvement. Something about this script is spawning zombies, though, because not only is the terminal notifying me of them but upon running the script manually I have to break to get back to a command line even though the output says the program has finished. Any other ideas?

---

### Post by hannaman on 2010-05-16
In a really quick look through the total I did notice a typo when the file gets gzipped.
```
OUTFILEGZ=$OUTFLIE.gz 
```
Should be
```
OUTFILEGZ=${OUTFILE}.gz 
```
Perhaps $OUTFILEGZ is empty, did you try to verify that $OUTFILEGZ actually contained something by echoing out the variable?
Also, the redirects look different than what I have used.  Normally I use:
```
ftp -n -v $FTPHOST **<<** ENDFTP
*ftp commands*
ENDFTP
```
But again, I more familiar with ksh than bash, so I could be wrong here.

---

### Post by MaddMatt on 2010-05-19
No improvements after those changes; I think the problem is loop-related as the echo statements printing the variables aren't running; so the program isn't even getting to that part before going zombie. Any other ideas?

Thanks,
Matt

---

### Post by hannaman on 2010-05-21
Maybe this has something to do with it:
```
$ HOSTFTPDIR="\"/Upload-Dir\""
$ echo $HOSTFTPDIR
"/Upload-Dir"
```
The quotes around /Upload-Dir seem unneeded.  Instead did you mean something like this:
```
$ HOSTFTPDIR=/Upload-Dir
$ echo "$HOSTFTPDIR"
/Upload-Dir
```
I don't think it finds the directory name with quotes.

---

### Post by MaddMatt on 2010-05-23
Yeah, unfortunately the target FTP server is a windows based server and has spaces in the directory names, so the quotes are mandatory. Anyway, I got fed up with the FTP part generating zombies twice a day processes twice a day so I reverted to the original and I'll just have to figure out another solution later. Thanks for the help!

Cheers, 
m

---

