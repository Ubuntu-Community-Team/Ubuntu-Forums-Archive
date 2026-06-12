---
title: "Help please can't get this working probably an easy fix!"
date: 2016-06-29
forum: Programming Talk
---

### Post by Simon_Benwell on 2016-06-29
Can anyone see why this isn't working please?


Below is a .sh file and if I run it I get...


--- UniFi Controller Backup Starting ---


Creating backup file 2016-06-29_unifi.tar.gz
tar: Cowardly refusing to create an empty archive
Try 'tar --help' or 'tar --usage' for more information.


--- UniFi Controller Backup Completed ---


I can write to the backup directory and create a txt file there so i know it can see it and can write there
I can ls the source folder and see files there


Sorry probably really simple I'm new to this!



```
#!/bin/bash


# CONFIGURATION


# Path to UniFi controller data directory
UCDDIR="/var/lib/unifi/data/";


# Path to backup directory
BKPDIR="/media/NTS-BACKUP";


# END CONFIGURATION
####################################################################################################
# PROGRAM


# Get current date
DATE=$(date +%Y-%m-%d)


# Start backup process
printf "\n--- UniFi Controller Backup Starting ---\n\n"
```

---

### Post by CharlesA on 2016-06-29
I do not see the tar command in the script.

It might also be a good idea to check to make sure /media/NTS-BACKUP is mounted before actually running the backup. I use mountpoint to do that.

EDIT: I checked one of the script I use for backups via tar and this is what I have:

```
tar --exclude='owncloud.log' -C /var/www/ -czf /backup/owncloud.tar.gz owncloud
```

---

### Post by howefield on 2016-06-29
Moved to the "*Programming Talk*" forum.

---

### Post by Simon_Benwell on 2016-06-29
Sorry half the message was cut off....

Can anyone see why this isn't working please?


Below is a .sh file and if I run it I get...


--- UniFi Controller Backup Starting ---


Creating backup file 2016-06-29_unifi.tar.gz
tar: Cowardly refusing to create an empty archive
Try 'tar --help' or 'tar --usage' for more information.


--- UniFi Controller Backup Completed ---


I can write to the backup directory and create a txt file there so i know it can see it and can write there
I can ls the source folder and see files there


Sorry probably really simple I'm new to this!




```
#!/bin/bash


# CONFIGURATION


# Path to UniFi controller data directory
UCDDIR="/var/lib/unifi/data/";


# Path to backup directory
BKPDIR="/media/NTS-BACKUP";


# END CONFIGURATION
####################################################################################################
# PROGRAM


# Get current date
DATE=$(date +%Y-%m-%d)


# Start backup process
printf "\n--- UniFi Controller Backup Starting ---\n\n"


# Stop UniFi service
service unifi stop


# Change directory to /
cd /


# Create backup folder if it doesn't exist
mkdir -p $BKPDIR


# Create UniFi backup file
printf "Creating backup file ${DATE}_unifi.tar.gz\n"
tar -C ${UCDDIR} -czf ${BKPDIR}/${DATE}_unifi.tar.gz


# Start UniFi service
service unifi start


# End backup process
printf "\n--- UniFi Controller Backup Completed ---\n\n"
```

---

### Post by CharlesA on 2016-06-29
There is no source listed for tar. See my above example.

---

### Post by Simon_Benwell on 2016-06-29
isn't this the tar bit? sorry to sound stupid
# Create UniFi backup file
printf "Creating backup file ${DATE}_unifi.tar.gz\n"
tar -C ${UCDDIR} -czf ${BKPDIR}/${DATE}_unifi.tar.gz

---

### Post by spjackson on 2016-06-29
Your tar command says to create a tar called ${BKPDIR}/${DATE}_unifi.tar.gz but you do not tell it what files and/or folders to put inside the tar file. See[ CharlesA's example]("http://ubuntuforums.org/showthread.php?t=2329243&p=13511000#post13511000") for how it should be done.

---

### Post by Simon_Benwell on 2016-06-29
sorry im new to this but does the "[COLOR=#000000][FONT=&quot]UCDDIR="/var/lib/unifi/data/";" tell the script what ucddir is 

like [/FONT][/COLOR][COLOR=#000000]tar -C ${UCDDIR} -czf ${BKPDIR}/${DATE}_unifi.tar.gz

doesn't that mean tar [/COLOR][COLOR=#000000][FONT=&quot]/var/lib/unifi/data/ -czf $[/FONT][/COLOR][COLOR=#000000][FONT=&quot]/media/NTS-BACKUP[/FONT][/COLOR][COLOR=#000000]/${DATE}_unifi.tar.gz

which mean create tar of [/COLOR][COLOR=#000000][FONT=&quot]/var/lib/unifi/data/ and store it [/FONT][/COLOR][COLOR=#000000][FONT=&quot]media/NTS-BACKUP[/FONT][/COLOR][COLOR=#000000]/ with file name  [/COLOR][COLOR=#000000]${DATE}_unifi.tar.gz[/COLOR]

[COLOR=#000000]am I not correct if not can someone should me with the script above hoe it should be write I have been give this script and told to modified the source and dest locations :/

Thank you so much for your help!   [/COLOR]

---

### Post by steeldriver on 2016-06-29
The -C just means "change to" the given directory - it doesn't say what you want it to do once it gets there

If you want to tar the contents of [COLOR=#000000]${UCDDIR} then you could probably do 

[/COLOR]```

[COLOR=#000000]tar -C [COLOR=#000000][COLOR=#000000]${UCDDIR} [/COLOR][/COLOR]-czf ${BKPDIR}/${DATE}_unifi.tar.gz [/COLOR][COLOR=#0000ff]**.**[/COLOR][COLOR=#000000] 
[/COLOR]
```
I think - but it would be more usual (and possibly more portable) to forget about -C and just do

```

[COLOR=#000000]tar -czf ${BKPDIR}/${DATE}_unifi.tar.gz [COLOR=#000000]${UCDDIR}[/COLOR]
[/COLOR]
```[COLOR=#000000]
[/COLOR]

---

### Post by CharlesA on 2016-06-29
> **steeldriver said:**
> 
I think - but it would be more usual (and possibly more portable) to forget about -C and just do

```

[COLOR=#000000]tar -czf ${BKPDIR}/${DATE}_unifi.tar.gz [COLOR=#000000]${UCDDIR}[/COLOR]
[/COLOR]
```[COLOR=#000000]
[/COLOR]

I tried that method and ran into some issues because I did not want the full directory structure preserved, which was why I used -C.

Another possible solution could be:

```
UCDDIR="/var/lib/unifi/";
tar -C $UCDDIR -czf DKPDIR/${DATE}_unifi.tar.gz data
```

---

### Post by Habitual on 2016-07-01
If it were me, I'd try
```
#!/bin/bash
UCDDIR="/var/lib/unifi/data"
BKPDIR="/media/NTS-BACKUP"
printf "\n--- UniFi Controller Backup Starting ---\n\n" 
service unifi stop

if [ -p /"$BKPDIR"  ]; 
    then # exists...
    printf "Creating backup file $(date +%Y-%m-%d)_unifi.tar.gz\n"
    echo tar -czf ${BKPDIR}/${DATE}_unifi.tar.gz ${UCDDIR}
    printf "\n--- UniFi Controller Backup Completed ---\n\n" $(service unifi start)
else 
    # does not exist...
    $(mkdir "$BKPDIR");
    printf "Creating backup file $(date +"%Y-%m-%d")_unifi.tar.gz\n"
    echo tar -czf ${BKPDIR}/${DATE}_unifi.tar.gz ${UCDDIR}
    printf "\n--- UniFi Controller Backup Completed ---\n\n" $(service unifi start)
fi
#EOF
```

Or I like functions as it allows some flexibility, so here's the function and the code to use it:
```
#!/bin/bash
UCDDIR="/var/lib/unifi/data"
BKPDIR="/media/NTS-BACKUP"
printf "\n--- UniFi Controller Backup Initializing...---\n\n" 

do_work()
{
    service unifi stop
    printf "Creating backup file $(date +%Y-%m-%d)_unifi.tar.gz\n"
    echo tar -czf ${BKPDIR}/${DATE}_unifi.tar.gz ${UCDDIR}
    printf "\n--- UniFi Controller Backup Completed ---\n\n" 
    service unifi start
}


if [ -p /"$BKPDIR"  ]; 
    then # exists...
    do_work
else 
    # does not exist...
    $(mkdir "$BKPDIR");
    do_work
#EOF
```

Remove "echo" from "echo tar" when you are happy with the results.
Hope that helps.

---

