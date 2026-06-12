---
title: "Bash Script for File Watcher Help"
date: 2010-05-25
forum: Programming Talk
---

### Post by climhazzard on 2010-05-25
Hi, I hope someone can help me out.  I'm trying to create a bash script that will evaluate a file to see when it was last changed and then send out an email.  So my idea is to create a script and use crontab to run it every few minutes to check the file.  I understand how to use crontab and have already setup mail, but I'm having trouble with finding the logic to actually evaluate the file.  Here's the non-working code I've got so far (the echo's will be replaced with syntax for sending out an email, this was just for testing):


```

#!/bin/bash
FILE=/home/evan/test.txt

if [ -f $FILE ];
then
	if [-mmin -10 $FILE];
	then
		echo "File $FILE exists and has been updated within the past 10 minutes"
	else
		echo "File $FILE exists but has not been updated within the past 10 minutes"
	fi
else
   echo "File $FILE does not exist"
fi

```

Any help is very much appreciated!

-Evan

---

### Post by Trumpen on 2010-05-25
-mmin is a find option and you can't use it with test.

Try with date, stat and some glue:

[php]#!/bin/bash
FILE=/home/evan/test.txt

if [ -f $FILE ];
then
	if (( $(stat -c %Y "$FILE") > $(date -d '10 minutes ago' +%s) ));
	then
		echo "File $FILE exists and has been updated within the past 10 minutes"
	else
		echo "File $FILE exists but has not been updated within the past 10 minutes"
	fi
else
   echo "File $FILE does not exist"
fi[/php]

---

### Post by climhazzard on 2010-05-25
Thank you so much Trumpen, this works perfectly!!

---

