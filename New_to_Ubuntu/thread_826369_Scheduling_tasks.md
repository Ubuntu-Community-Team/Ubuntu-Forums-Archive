---
title: "Scheduling tasks"
date: 2008-06-11
forum: New to Ubuntu
---

### Post by UnWarierMage224 on 2008-06-11
Hi folks, 

Three things I'd like to do:

1. Find an easy (preferably GUI) way to schedule tasks.
2. Set up Avast AV to update itself weekly, automatically. 
3. Have Avast perform a virus scan weekly, automatically.

I believe these have something to do with crontab/cron jobs but I've got no clue how to set them up. 

Thanks, 

-'Mage

---

### Post by bruce89 on 2008-06-11
*cron* is the thing that does tasks. However, virus scanning is pointless.

---

### Post by iaculallad on 2008-06-11
> **UnWarierMage224 said:**
> 

1. Find an easy (preferably GUI) way to schedule tasks.

-'Mage

Try GNOME-Scheduler (GUI):

```
sudo apt-get install gnome-schedule
```

---

### Post by powerpleb on 2008-06-11
I think anacron is the way to go on desktop systems as it runs the scheduled task a specified time after the OS loads (e.g. weekly, 30 mins after booting) rather than at a specific time (every 7 days at 7.35pm *what if the computer is off?*).

This explains it quite well:
[http://linuxgazette.net/104/odonovan.html](http://linuxgazette.net/104/odonovan.html)

---

### Post by ibuclaw on 2008-06-11
Simpler than that.

Just make a script and put it in the "**/etc/cron.weekly/**" folder.

ie: For avast
Open up a file
```
sudo gedit /etc/cron.weekly/avastscan
```
And paste in
```

#!/bin/bash

# Update Avast Virus Database
avast-update

# cd / and Start Scan (Here default is set to repair... -p=1 to set to delete)
cd / && avast -c -p=3 -t=A -r=/tmp/avastscan.log

# Mail the infected results to you.
cat /tmp/avastscan.log | mail -t **<yourname>** -s "avastscan infected log"

# Remove the temp file created in this script.
rm /tmp/avastscan.log

```
Replace <yourname> with your username (if you want a mail of the list of infected files).

Save+Quit, then mark it executable.
```
sudo chmod +x /etc/cron.weekly/avastscan
```
Regards
Iain

---

### Post by UnWarierMage224 on 2008-06-15
OK, cool. 

Thanks for the pointers, everyone. 

-'Mage

---

### Post by ibuclaw on 2008-06-15
May I just add that if you are going to use a cronjob script similar to mine, it is pretty much pointless to scan the **entire** root "/" folder.

I recommend that you just can the /home directories.

```
cd /home && avast -c -p=3 -t=A -r=/tmp/avastscan.log
```

Regards
Iain

---

### Post by voldemorte on 2010-10-24
Is a reboot required after doing this??  > **ibuclaw said:**
> Simpler than that.

Just make a script and put it in the &quot;**/etc/cron.weekly/**&quot; folder.

ie: For avast
Open up a file
```
sudo gedit /etc/cron.weekly/avastscan
```And paste in
```

#!/bin/bash

# Update Avast Virus Database
avast-update

# cd / and Start Scan (Here default is set to repair... -p=1 to set to delete)
cd / && avast -c -p=3 -t=A -r=/tmp/avastscan.log

# Mail the infected results to you.
cat /tmp/avastscan.log | mail -t **<yourname>** -s &quot;avastscan infected log&quot;

# Remove the temp file created in this script.
rm /tmp/avastscan.log

```Replace <yourname> with your username (if you want a mail of the list of infected files).

Save+Quit, then mark it executable.
```
sudo chmod +x /etc/cron.weekly/avastscan
```Regards
Iain

---

