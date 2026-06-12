---
title: "cron job"
date: 2014-01-02
forum: New to Ubuntu
---

### Post by tbsoft2001 on 2014-01-02
I have a script to back up my music files via rsync. I'd like to automate this so it runs every hour so I don't have to do it by hand. The script works fine. I cannot figure out what I'm doing wrong in this cron job command . . . the name of the script is accurate as is the location . . . I created the job using 

crontab -e

etc.....

```

11 * * * * /home/nameofcomputer/Desktop/musicbackup.sh

```

That line is all that is in the cron job file . . . 

do I need a shebang line? what am I missing?

I had this automated previously as a cron job and cannot figure out what's different

TIA

---

### Post by Kirk Schnable on 2014-01-02
Is the script executable?  If not, cron job will not run. 

You can make the script executable by running:
[B]chmod +x /path/to/script.sh
[/B]

---

### Post by papibe on 2014-01-02
Hi tbsoft2001.

Is that the correct path to the script?

Could you post the content of the script?

Regards.

---

### Post by Dave_L on 2014-01-02
For debugging purposes:

```
11 * * * * sh -vx /home/nameofcomputer/Desktop/musicbackup.sh >/home/nameofcomputer/Desktop/musicbackup.log 2>&1
```

When you run a script in this manner (with the "sh" command), the file doesn't need to be executable.

---

### Post by tbsoft2001 on 2014-01-03
As I said, the script works fine.

---

### Post by tbsoft2001 on 2014-01-03
[I][B]"[COLOR=#000000]. the name of the script is accurate as is the location . ."


[/COLOR][/B][/I]**[COLOR=#000000][/COLOR]**[COLOR=#000000]&#8203;from my original post[/COLOR]

---

### Post by Dave_L on 2014-01-03
Did you try my suggestion? The contents of musicbackup.log may help you figure out what's wrong.

---

### Post by tbsoft2001 on 2014-01-03
Hi. Yes, I just tried what you suggested. I assumed you wanted me to create a new cron job so I did that and set it to run every hour at 11 minutes past the hour... as far as I can tell, the time came and went and nothing happened and no log file was created.

```

11 * * * * sh -vx /home/dbcooper-dell/Desktop/musicbackup.sh >/home/dbcooper-dell/Desktop/musicbackup.log 2>&1


```

For the non-believers, this is the script file:

```

#!/bin/bash

rsync -avz /media/MUSIC1/ --force --ignore-errors /mnt/musicbackup


```

As I said, it runs fine when I execute it "by hand".

Also, is there a way to use my user name to log in or be identified on these forums - I have been a member for at least a decade yet with the new system I seem to have lost those stats.....:-)

thanks

---

### Post by Dave_L on 2014-01-03
Try looking at /var/log/syslog, either manually or with the log viewer, and see if there are any "cron" messages related to your script.

Here's a quick way of doing that ("sudo" might not be needed):
```
sudo grep -i cron /var/log/syslog
```

For the forum user name problem, make a post about it in the Resolution Centre and one of the staff will help you:
[http://ubuntuforums.org/forumdisplay.php?f=123](http://ubuntuforums.org/forumdisplay.php?f=123)

---

### Post by tbsoft2001 on 2014-01-03
Thank you for your prompt reply. The line items from the log which appear pertinent are:```
Jan  3 11:11:01 dbcooper-dell-desktop CRON[7743]: (root) CMD (dbcooper-dell /home/dbcooper-dell/Desktop/musicbackup.sh)Jan  3 11:17:01 dbcooper-dell-desktop CRON[7869]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
```which seems to indicate the cron job is running as root (?) - which I don't understand since (I thought) I created it as a user . . .

---

### Post by The Cog on 2014-01-03
You probably need a -c argument to sh, like this:
```
11 * * * * sh -vxc /home/dbcooper-dell/Desktop/musicbackup.sh >/home/dbcooper-dell/Desktop/musicbackup.log 2>&1
```

And you may need to put the full path to everything in your scipt, e.g. "/usr/bin/rsync" instead of just "rsync".

---

### Post by Dave_L on 2014-01-03
If you list the cron table from your user account, does the entry show up?

```
crontab -l
```

To see root's crontab:

```
sudo crontab -l
```

---

### Post by tbsoft2001 on 2014-01-03
I checked /etc/cron.hourly and this  is the text of the musicbackup.cronjob  there:```
0 * * * * dbcooper-dell /home/dbcooper-dell/Desktop/musicbackup.sh
```

---

### Post by tbsoft2001 on 2014-01-03
There is no cron job listed for my user name i.e. doing```
crontab -l
``````
sudo crontab -l
```spits out the most-recent cron job i.e.```
11 * * * * dbcooper-dell /home/dbcooper-dell/Desktop/musicbackup.sh
```and I don't know how/why

---

### Post by tbsoft2001 on 2014-01-03
I deleted the root cron job; again, I'm not sure how it got there. Then I deleted every other file related to cron jobs.

Then, I created a new cron job and in a flash of . . . something, decided to save it to the default location with the default name given when I run

```

crontab -e

```

and create a cron job. It goes to /tmp and has an incomprehensible name.

However, the job now works with the basic command I started with. I checked it in the log and I placed a file in the folder to be backed up to see if it would be copied to the back up folder - and it was. So, Houston, it looks like we're good to go.

Thanks to those who helped.

---

### Post by The Cog on 2014-01-03
That's good news.

FYI, crontab -e creates a temporary file for you to edit.Then it then performs some sanity checking on your work before it is willing to overwrite the real crontab file with it.

---

### Post by tbsoft2001 on 2014-01-03
"[COLOR=#000000]FYI, crontab -e creates a temporary file for you to edit.Then it then performs some sanity checking on your work before it is willing to overwrite the real crontab file with it."
[/COLOR]
Thank you for that. I went back and edited the crontab file saving it again to the temporary location the program assigns ... then I saved it to a file on my desktop and when I exited I got the message that the job had been created and I checked with 

```

crontab -l

```

to make sure the job is there and it is.

Of course the real deal is whether it runs at the appointed time - but I'm pretty sure it's good.

Thanks again.

---

