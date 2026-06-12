---
title: "Sed Multiple Files insert apostrophe"
date: 2014-01-07
forum: Programming Talk
---

### Post by RIK312 on 2014-01-07
Hello all :KS

I have this current sh code
```
DELETE=`$MEGASYNC --username $USER --password $PASSWORD --dryrun  --reload --download --local $LOCALDIR --remote $REMOTEDIR | sed 's/F  '$SEDLOCALDIR'/'$SEDREMOTEDIR'/g'`
```
an example of output of $DELETE is
```
/Root/W/my file 1.txt /Root/W/my file 2.txt /Root/W/my file 3.txt
```
but i need
```
"/Root/W/my file 1.txt" "/Root/W/my file 2.txt" "/Root/W/my file 3.txt"
```
what is the correct sed syntax for get the apostrophe?
Thanks so much

---

### Post by ian-weisser on 2014-01-07
Escape the quote (") char using a backlash (\) 
Example replacing all the 't' chars in a string with '"' chars:
```
$ echo example string | sed 's/t/\"/g'
example s"ring
```

---

### Post by sisco311 on 2014-01-07
Welcome to the forums!

Please check out:
[http://mywiki.wooledge.org/Arguments](http://mywiki.wooledge.org/Arguments)
and BashFAQ 020 (link in my signature).

 You didn't post the actual command which you use. Does it have an option to print null terminated list of file names?

---

### Post by RIK312 on 2014-01-07
Finally I have fixed the code from myself :KS Anyone need the correct code is

```
#!/bin/sh
USER="###"
PASSWORD="###"
MEGASYNC='/usr/local/bin/megasync'
MEGARM='/usr/local/bin/megarm'
LOCALDIR="/local/dir"
REMOTEDIR="/Root/Dir"
SEDLOCALDIR="\/local\/dir"
SEDREMOTEDIR="\/Root\/Dir"
BACKUP_TIME=`date +%c`
LOG="/usr/local/bin/Mega - "`date +%d" "%m" "%y`".txt"
DELETE=`$MEGASYNC --username $USER --password $PASSWORD --dryrun --reload --download --local $LOCALDIR --remote $REMOTEDIR | sed 's/F '$SEDLOCALDIR'/'$SEDREMOTEDIR'/g'`
echo "$DELETE" | while read line ; do
if [ ! -z "$line" ] ; then
$MEGARM --username $USER --password $PASSWORD "$line"
echo "[$BACKUP_TIME] File Removed "$line"" >> $LOG
fi
done
$MEGASYNC --username $USER --password $PASSWORD --no-progress --local $LOCALDIR --remote $REMOTEDIR >> $LOG
echo "[$BACKUP_TIME] Synchronization to MEGA Done!" >> $LOG
```
Thanks all for the help! Have a nice day

---

