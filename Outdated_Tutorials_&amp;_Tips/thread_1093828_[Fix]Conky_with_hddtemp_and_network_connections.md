---
title: "[Fix]Conky with hddtemp and network connections"
date: 2009-03-12
forum: Outdated Tutorials &amp; Tips
---

### Post by XanTrax on 2009-03-12
Hi everyone,

I noticed when using Conky and hddtemp application that most conky scripts will query hddtemp through 

```

nc localhost <hddtemp_port>

```

and would populate netstat command with a whole ton of TIME_WAIT connections.  I have developed a fix for this.

1.) First, edit the hddtemp script where you report the temperature to look something like this:

```

Temperature: ${alignr}${exec cat /etc/hddtmp_out }

```

Then:

```

sudo touch /etc/hddtmp_out

```

Then, utilize this script or create a simliar to generate the same effects:

```

#!/bin/bash

date=`date`
touch /root/logs/gettemp.log

/usr/sbin/hddtemp /dev/sda1 | cut -d ":" -f3 > /etc/hddtmp_out
if [ $? -eq 0 ]; then
	echo "Command completed successfully"
elif [ $? -gt 0 ] || [ $cmd != " " ]; then
	echo "Caught error"
fi

temp=`hddtemp /dev/sda1 | cut -d ":" -f3`
log=`echo Get temp finished @ $date reporting $temp >> /root/logs/gettemp.log`

exit 0

```

What this script does:

First it gets the date and touches gettemp.log in /root/logs/ to ensure it is there.  Then, it executes the hddtemp executable querying the appropriate hard drive.  Make sure to change to your appropriate hard drive (read hddtemp manual).  The script then parses out the temperature and outputs it to /etc/hddtmp_out (hint: cat /etc/hddtmp_out from the conky script).  Finally, for logging and error reporting purposes, it outputs to the gettemp.log file in the root directory.  This was more or less used when I was debugging so you can remove it if you like.  You can place that in /usr/local/bin for easy access as that is how I created the cron job (read below). 

Then create a cron job to run every minute.  This wont be too intensive on the system seeing as to query the temperature through the cron job is about as equal as running the netcat command.

```

sudo su -
crontab -e

```

Add this line:

```

*	*	*	*	*	test -x /usr/local/bin/gettemp && ( sudo /usr/local/bin/gettemp )

```

This will create a cron job to execute every minute to report and output to the hddtmp_out file in /etc.

---

### Post by XanTrax on 2009-03-17
I dont know the rule on this but this took five days to get approved so Im gonna go ahead and bump it.  If I am wrong, please tell me.

---

### Post by tturrisi on 2009-03-19
I just updated my Conky HDDTEMP HowTo here.
Netcat is no longer necessary, hddtemp is now a built in variable of Conky.
If hddtemp is running as a daemon, it can be accessed directly by non-root users.
[http://ubuntuforums.org/showthread.php?t=282353](http://ubuntuforums.org/showthread.php?t=282353)

---

### Post by XanTrax on 2009-03-19
> **tturrisi said:**
> I just updated my Conky HDDTEMP HowTo here.
Netcat is no longer necessary, hddtemp is now a built in variable of Conky.
If hddtemp is running as a daemon, it can be accessed directly by non-root users.
[http://ubuntuforums.org/showthread.php?t=282353](http://ubuntuforums.org/showthread.php?t=282353)

Awesome, then my time was wasted :p.  How long has hddtemp been implemented directly?

---

### Post by loomsen on 2009-03-19
I'd still prefer smartctl, simply because a smartctl query doesn't cause DiskIO, hddtemp does.

I had some issues with high load cycle counts in prior versions of ubuntu, no need for another process waking my disk up periodically.

Just my 2 ct


Btw, smartctl is part of the pkg smartmontools...

sudo apt-get install smartmontools.

---

### Post by XanTrax on 2009-03-20
> **loomsen said:**
> I'd still prefer smartctl, simply because a smartctl query doesn't cause DiskIO, hddtemp does.

I had some issues with high load cycle counts in prior versions of ubuntu, no need for another process waking my disk up periodically.

Just my 2 ct


Btw, smartctl is part of the pkg smartmontools...

sudo apt-get install smartmontools.

Ill give them a try, thank you.

---

### Post by binbash on 2009-03-20
Good work!

---

### Post by XanTrax on 2009-03-20
> **binbash said:**
> Good work!

Thank you :)

---

