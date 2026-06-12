---
title: "Converting bash to batch"
date: 2011-10-05
forum: Programming Talk
---

### Post by layr on 2011-10-05
Never had any experience with batch programming. How difficult would be converting this to batch:
```
# METAR bash script for Win/bash
while :
do
	current_mins=$(date -u "+%M")		
	current_hours=$(( 10#$(date -u "+%H") ))	# Note the -u <-- UTC time
	if [[ $current_hours == 0 ]]; then
	   current_hours=24
	fi
	metar_hours=$(( 10#$(cat ~/METAR/EETU.txt | cut -c8-9) ))
	if [[ "$(echo {50..59})" =~ "$current_mins" && "$metar_hours" == "$(($current_hours-1))" ]] || [[ "$current_hours" != "$metar_hours" && "$metar_hours" != "$(($current_hours-1))" ]];then
		if ping -n 1 www.google.com; then
			curl -s 'http://weather.noaa.gov/pub/data/observations/metar/stations/EETU.TXT' | sed -n 2p > ~/METAR/EETU.txt
		fi
	fi
	sleep 60
done
```
It's possible to run it in cygwin, but as this script needs to be looped, there's no way running it silently, i.e. windowless.
(If anyone has way too many spare time, it would be appreciated  :) )

---

### Post by WasMeHere on 2011-10-05
Maybe you can make a cronjob of it using *crontab*.

Here are some good examples how-to set up crontab. I have used these tutorials to set up a talking clock.

[_Cron and Crontab usage and examples_]("http://www.pantz.org/software/cron/croninfo.html")
[_Linux Crontab: 15 Awesome Cron Job Examples_]("http://www.thegeekstuff.com/2009/06/15-practical-crontab-examples/")

See also man crontab

---

### Post by collisionystm on 2011-10-05
What does your script do?

---

### Post by layr on 2011-10-05
> **Olle Wiklund said:**
> Maybe you can make a cronjob of it using *crontab*.
Is setting cronjobs possible in Windows using cygwin? As i understand, linux kernel is needed for that!?


> **collisionystm said:**
> What does your script do?
This script is used for downloading current METARs. METAR is weather information for specific airport, here it is for EETU (ICAO abbreviation for Tartu airport here in Estonia).
Script is ran every 60 seconds; then it compares 8th and 9th digits from file 'EETU.txt' (which is METAR release hour) against current system clock hour. As new METARs are published every hour at HH:50, the metar currently saved in EETU.txt gets expired as current system time minutes are 50-59 **AND** metar/file hour value is current hour minus one **OR** current hours don't equal to metar/file hours **AND** metar hours are not equal to current hours minus one.
    If METAR is found to be old, script checks whether there is internet connection; if it is true, downloads (hopefully) new METAR and saves it's second line to ~/METAR/EETU.txt.
    As the .bat wouldn't be for myself, more robust version without comparing the release time and connection checking would also do : )

PS. the ```
if [[ $current_hours == 0 ]]; then
	   current_hours=24
```
part is needed for the current_hours-1 comparison (otherwise 00-1 wouldn't equal to 23).

---

### Post by karlson on 2011-10-05
> **layr said:**
> Is setting cronjobs possible in Windows using cygwin? As i understand, linux kernel is needed for that!?

Windows Task Scheduler is the native equivalent, but I think there is a version of cron that is available in CYGWIN.

Also, keep in mind that Linux/UNIX philosophy is different from Windows and cron does not require Linux/UNIX kernel to be running.  CRON is a "service" in Windowspeak.

---

### Post by WasMeHere on 2011-10-05
> **layr said:**
> Is setting cronjobs possible in Windows using cygwin? As i understand, linux kernel is needed for that!?

It was several years since I used cygwin (and I never tried to use cron). I guess it would be easy for you to find out if cron is part of cygwin: [FONT="Courier New"][SIZE="3"]which cron[/SIZE][/FONT]

If cygwin is able to run background jobs, you could do something like the following example to start your job. If you close the terminal window after issuing the job, it would not litter your desktop.
```
echo Use the following command to stop "$0"
while test 1 ; do espeak 'snooze' >/dev/null 2>/dev/null;sleep 5;done & pid=$!
echo kill "$pid"

```

Good luck
Olle

---

### Post by WasMeHere on 2011-10-05
... or even better: run Ubuntu :-)

either by itself or in a virtual machine. That way you will have much more features of linux available.

---

### Post by layr on 2011-10-05
> **Olle Wiklund said:**
> ... or even better: run Ubuntu :-)

either by itself or in a virtual machine. That way you will have much more features of linux available.
Thanks, i'll try to get the cron running.
Second recommendation isn't acceptable though - i am running Ubuntu myself, i need to convert that script for the computer at the Academy where i'm studying.

---

### Post by layr on 2011-10-06
Okay, managed to get this far:

Installed cron and cygrunsrv.

Tried installing cron as Windows service using commands:```
cygrunsrv -I cron -p /usr/sbin/cron -a -D


```which yielded in error (Win32 error 1062: the service has not been started)

and
```
cygrunsrv --install cron --path /usr/sbin/cron --args -n
``` 

which gave no error.

Started cron with 'cygrunsrv --start cron', to which i got "cygrunsrv: Error starting a service: QueryServiceStatus: Win32 error 1062: The service has not been started"

Second time i tried (removed cron previously), cygrunsrv --start cron didn't give any errors, but cron wasn't running either. Running 'net start cron' in Windows cmd prompt gave then "The requested service has already been started. More help is available by typing NET HELPMSG 2182."
Web is full of similar problems, but no definite solution wahatsoever.

---

### Post by layr on 2011-10-06
Edit 2:
Got it finally running. Cron had to be set up via 'cron-config'.
This tutorial helped: [http://linuxbites.wordpress.com/2010/06/28/starting-crontab-in-cygwin/](http://linuxbites.wordpress.com/2010/06/28/starting-crontab-in-cygwin/)
My recommendation for future searchers would be forgetting about the methods shown in my previous post and going with the cron-config.

PS thanks for the cron idea, Olle!

---

