---
title: "Grab latest log file with bash"
date: 2009-04-29
forum: Programming Talk
---

### Post by easybake on 2009-04-29
Here is the situation I have got my self into: My main goal is to monitor the temperatures of my desktop(running Windows XP) with my laptop(running Ubuntu).

Currently I have my XP Desktop updating a log file with the temperatures. I then use my laptop to grab the log file using sftp.

However, this is where I run into a problem, the log files are created daily. The have titles like "CT-Log 13-24-59 May-28-2009.csv" (The 13-24-59 means 1:24pm and 59 seconds, which is irrelevant).

In the bash script I'm making, I only want to deal with the newest log file. 

Is there some way within the script to reference only the newest log file in a folder?

---

### Post by unutbu on 2009-04-29
When you run the bash script, are you guaranteed to find a log file with today's date, or might the latest log be from some prior date?

---

### Post by easybake on 2009-04-29
Thanks! I think I see where you are going with that... and the log file should be reset everyday.

would I be on the right track with this:

```

#!/bin/sh
MONTH=`date +%b`
DAY=`date +%d`
YEAR=`date +%Y`

TEST=`tail --lines 1 /home/easybake/CT-Log*$MONTH-$DAY-$YEAR.csv`

echo $TEST
```

I'm unsure about the * in the TEST line. When I ran it seemed to work.

---

### Post by unutbu on 2009-04-29
Sure, that looks good. 
You could also use 
```

TODAY=$(date '+%b-%d-%Y')
TEST=$(tail --lines 1 /home/easybake/CT-Log*"$TODAY".csv)
```

if you don't need MONTH, DAY and YEAR individually later in your script.

---

### Post by easybake on 2009-04-29
Thank you. Your's looks much cleaner. 

But on second thought I may not get a log file for the current day if I am using the computer after midnight. Is there a better way to accomplish this. By either taking the current day or the day closest to it?

Edit: but the logs would only ever be 1 day behind if ever.

---

### Post by unutbu on 2009-04-29
If you put the log files in a directory of its own, say, in /home/easybake/Logs

then you could list them sorted according to modtime:
```

ls -1t
```

and pick off the name of the most recent log with

```
ls -1t | head -n 1
```

---

