---
title: "Problems with lftp and scheduled tasks"
date: 2011-11-19
forum: New to Ubuntu
---

### Post by e4uforums on 2011-11-19
I've been working on this for a while now and I'm stuck at the last part.  I just crashed into a brick wall and was hoping someone could help me back to my feet.

I have a server at home running Ubuntu 10.04.  I have written some scripts using lftp to mirror some directories on my webservers to directories on my Ubuntu machine.  Backups made easy, right?

Below is an example of my script.  If I double click the script and choose "Run in Terminal" the script will run as I expect it would.  It connects to the ftp server, mirrors the directories and closes the terminal window.  Just what I want.

However, when I have the task setup through Scheduled Tasks, it'll bring up the Terminal but just stops at a lftp prompt with a blinking cursor - it doesn't actually complete the rest of the command.

I've tried running it via Scheduled Task as root, but that didn't work either (and I wasn't thrilled about running a script as root anyways).

Like I said, the wall and I are now one.  Can anyone give me a hand?  

Thank you very much!

```

#!/bin/bash

# Simple backup script for flat file site.

NOW=$(date +"%F")
FILE="/home/*USERNAME*/Desktop/backup_scripts/logs/$NOW.logfile.txt"

lftp -u *HOSTNAME*,*PASSWORD* ftp://*IP.ADDRESS.HERE* -e "mirror --verbose /*PATHTO*/*REMOTEBACKUP*/ /media/sdb1/*PATHTO*/*LOCALBACKUP*/ ;exit 0"

echo "backup and sync completed at `date`" >> $FILE

exit

```

---

