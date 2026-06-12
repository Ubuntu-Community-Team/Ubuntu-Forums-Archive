---
title: "Email trigging program?"
date: 2011-01-12
forum: Programming Talk
---

### Post by kaspar_silas on 2011-01-12
Hello,

Does anyone know how to make the arrival of an email into an imap folder trigger a program to run. I initially tried evolution via it's message filtering but that didn't work.

[http://ubuntuforums.org/showthread.php?p=10347535#post10347535]("http://ubuntuforums.org/showthread.php?p=10347535#post10347535")

So I'll try and sort out evolution. However I thought I would ask here if there was a simpler option? 

Thanks for any help

---

### Post by kaspar_silas on 2011-01-14
Okay so I figured out how to do this myself. Just on the off chance this is useful to someone else here is the solution. It's basically just watching the evolution archive file size and triggering if that changes. It's not elegant and I am sure there are better options but here you go:

Firstly in evolution I made an offline folder and added a mail filter to divert emails with a magic word in the subject.

Next I wrote a little bash script to trigger a program if the evolution log file relating to my offline folder increases. Here is the script: 

```
#!/bin/bash
#FILEWATCH
DATA="~/.local/share/evolution/mail/local/AutoReplyLog"
TEMP="~/.AutoReplyLogSize"
PROGRAM="~/bins/CONVERTER"

#Check old size logfile exists
if [ ! -f "$TEMP" ]
then
	echo "0" > $TEMP
	exit
fi

#Get new and old file size
NEW=$(stat -c%s "$DATA")
OLD=`cat $TEMP`

#Calculate file difference
DIF=`echo "$NEW-$OLD" | bc`

#If for some reason the older is bigger rewrite it
if [ $DIF -lt "0" ]
then
	echo $NEW > $TEMP
	exit
fi

#Run the mighty program
echo $NEW > $TEMP
$PROGRAM
exit
```

I then run this in the background repeating every 30 seconds.

$ while true;do FILEWATCH;sleep 30;done

Hurray! Now if a valid email arrives the converter program runs. For me this is a short python script that strips the last message from evolution's email log, reforms the attachments, does some analysis on them then emails back the result.

---

### Post by kaspar_silas on 2011-01-14
Removed

---

