---
title: "what user does the cron daemon run as"
date: 2007-09-04
forum: Programming Talk
---

### Post by prospero527 on 2007-09-04
I was just wondering if anyone knows what user the cron daemon runs as when it executes scripts.  I thought it might be the user whose crontab is being run but this doesn't seem to be the case.  I don't see a cron user in /etc/passwd.  My best guess is that it runs as the daemon user.  Any insight would be greatly appreciated.

---

### Post by nanotube on 2007-09-04
> **prospero527 said:**
> I was just wondering if anyone knows what user the cron daemon runs as when it executes scripts.  I thought it might be the user whose crontab is being run but this doesn't seem to be the case.  I don't see a cron user in /etc/passwd.  My best guess is that it runs as the daemon user.  Any insight would be greatly appreciated.

stuff from the user's crontab runs as the user. since you said that it doesn't seem to be the case, i checked - i created a cron job that sleeps for 60 secs, so i could look at the process in the process list. :)

here's the output:
```
$ ps alx |grep sleep
4  1000 23705 23704  22   0   1712   476 wait   Ss   ?          0:00 /bin/sh -c sleep 60
0  1000 23706 23705  23   0   2800   620 -      S    ?          0:00 sleep 60
0  1000 23751 23590  17   0   2884   748 -      R+   pts/3      0:00 grep sleep

```

the sleep 60 process is running with UID 1000, which is my UID.

what led you to believe that it runs as some other user?

---

### Post by prospero527 on 2007-09-04
The thing that led me to believe it didn't is that i have a backup script that is owned by a user i created for the backup and the directory that it backs up files to has permissions rwxr--r-- and is owned by the backup user.  I scheduled the script to run every night via its crontab.  The logs show the script running but the backup file is not created.  So I figured it was a permissions thing.  I changed the permissions of the directory to be world writeable and sure enough the file got created.  So I figured, Okay i'll change the actual script to be suid and since it is owned by the backup user i can reset the permissions back to 744  but i'm back to the same situation. the logs show the script running but no file is created.

So that's why I said it doesn't seem to be the case.  I didn't even think about testing with a program that calls sleep().  Good idea.  There must be something trivial that I am missing.

---

### Post by prospero527 on 2007-09-04
Here's my code in case it helps
```

#!/usr/bin/perl -w
use strict;

my $now = localtime();
$now = join('-', split(/ /, $now));

# dump the database and bzip2 it
system("mysqldump --add-drop-table -u ***** -p***** SAOT | bzip2 -c > /var/backups/saot/saot_$now.sql.bk.bz2");

# open backup directory
opendir(DIR, '/var/backups/saot');

# get all the directory entries
my @files = readdir(DIR);

# go through each file to see if it is older than 30 days
# if it is then delete it
for my $file (@files) {
        $file = '/var/backups/saot/' . $file;
        if (-f $file && $file ne 'saotbackup.pl') {
                my $time = (stat($file))[8]; # file mtime (time of last write) since epoch

                # if file mtime is less than current time -30 days (2592000 seconds) remove file
                if ($time < (time() - 2592000)) {
                        system("rm $file");
                }
        }
}

open(LOG, ">> /var/log/saot/saotbackup.log");
print LOG "backed up $now\n";
close LOG;

```

---

### Post by prospero527 on 2007-09-04
never mind i solved the problem :D

---

### Post by nanotube on 2007-09-04
> **prospero527 said:**
> never mind i solved the problem :D

cool. :) care to share the solution for the benefit of future generations? :)

---

### Post by prospero527 on 2007-09-04
heh well really nothing surprising.  I noticed there was already a user on the system called backup, I changed the ownership of the /var/backups/saot/directory to be owned by backup.  The actual script is still setuid. But now it works like a charm with permissions of 744 on the directory.  Maybe something was odd that I missed before cause I didn't really change anything except the file owner.  And of course i edited backup's crontab.  Probably just user error on my part from the beginning.  Thanks for the reply.

---

