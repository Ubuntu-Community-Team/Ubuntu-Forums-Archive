---
title: "Shell Script Issue - Need Advice"
date: 2009-01-28
forum: Programming Talk
---

### Post by Barnicle on 2009-01-28
I have a script that moves files to their designated folder using crontab, but some days I find that the files are missing (deleted). I want to run my script by you guys to see if you see any flaws. Basically, I have 7 folders, one for each day of the week, and 4 other folders for previous weeks. Once the daily backup file is FTP'ed over, the script will run and depending on the day, it will move the .rar file to it's designated folder. On Monday's, it will deleted the fourweeksago folder, and move all the files over by one week, and take Sunday and put it into the oneweekago folder. Daily, it will remove the previous file that was in the weekday folders, and replace it with the newly FTP'ed file for the day.

```
#! /bin/bash
declare day

day=`date '+%A'`

if [ "$day" == "Monday" ]; then
        rm -f ~/fourweeksago/*.*
        mv ~/threeweeksago/*.* ~/fourweeksago
        mv ~/twoweeksago/*.* ~/threeweeksago
        mv ~/oneweekago/*.* ~/twoweeksago
        mv ~/sunday/*.* ~/oneweekago
        mv ~/*.rar ~/sunday
elif [ "$day" == "Tuesday" ]; then
        rm -f ~/monday/*.*
        mv ~/*.rar ~/monday
elif [ "$day" == "Wednesday" ]; then
        rm -f ~/tuesday/*.*
        mv ~/*.rar ~/tuesday
elif [ "$day" == "Thursday" ]; then
        rm -f ~/wednesday/*.*
        mv ~/*.rar ~/wednesday
elif [ "$day" == "Friday" ]; then
        rm -f ~/thursday/*.*
        mv ~/*.rar ~/thursday
elif [ "$day" == "Saturday" ]; then
        rm -f ~/friday/*.*
        mv ~/*.rar ~/friday
elif [ "$day" == "Sunday" ]; then
        rm -f ~/saturday/*.*
        mv ~/*.rar ~/saturday
fi
```

---

### Post by Cracauer on 2009-01-28
Didn't we have the same thread 2 weeks ago? :)

Still looks as backwards as back then.

What's the question, anyway?

---

### Post by Barnicle on 2009-01-28
I think it was a crontab question, or a slightly different script ;)

The question is, does this script do what it is suppose to do, or am I missing something where it's deleting a file?

For example, today is Wednesday, so I went to check if the tuesday backup was moved to the tuesday folder, but it was not there. Am I missing something with this script that would cause it to delete the tuesday file?

---

### Post by Barnicle on 2009-02-02
I've got a problem with this script. I got a syntax error today when I ran it manually.

```
$ ./autoback.sh
./autoback.sh: line 25: syntax error near unexpected token `elif'
./autoback.sh: line 25: `elif [ "$day" == "Saturday" ]; then'
```

Do I not need the ';' in my if statements?

---

