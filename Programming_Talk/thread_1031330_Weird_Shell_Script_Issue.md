---
title: "Weird Shell Script Issue"
date: 2009-01-05
forum: Programming Talk
---

### Post by Barnicle on 2009-01-05
Hi there,

I have a shell script (autoback.sh) that isn't executing even after doing 'chmod a+x autoback.sh'. I type autoback.sh to execute it, and I get an error saying:

```
root@backupserver:~# autoback.sh
bash: autoback.sh: command not found
```

Why is this happening? I know it has to be something simple! The only thing I have changed since the last time this script was working was that I consolidated two scripts into one to just have one shell script. This is the script I'm trying to run:

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

### Post by Cracauer on 2009-01-05
./autoback.sh

Requires execute permissions first.

BTW, you might want to consider a case statement.

---

### Post by Barnicle on 2009-01-05
Thanks, I just remembered that I had to have './' before. What would you suggest for a case statement?

---

### Post by Martin Witte on 2009-01-05
```
#!/bin/bash

# A case statement is useful if you have more options to execute
# different parts of code

day=Sunday

case $day in
	Monday)
		echo day is monday
		;;
	Tuesday)
		echo day is tuesday
		;;
	# put other days here in the same manner
	*)
		echo $day is not valid
esac

# But in your case something like this might be an idea,
# as most days you do more or less the same actions
# The 'tr' command translates sets of characters, see 'man tr'
# for more information

day=$(echo $day|tr  '[:upper:]' '[:lower:]')

echo $day

if [[ $day == monday ]]; then
	echo do monday actions
else
	rm  ~/$day/*
	# etc
fi
```

---

