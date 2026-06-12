---
title: "scripting problem in bash"
date: 2010-02-22
forum: Programming Talk
---

### Post by ibizatunes on 2010-02-22
Im trying to created a script that will clear out /var/logs/ ,and email me when it run
If there a way of converting the FILE_SIZE varaible to a human number like 4GB or 500mb?


```
#!/bin/sh
DISK_UTIL=`df -h | grep /var/logs/ | awk '{ print $5 }'`

#admin email account
ADMIN="admin@company.com"

#hostname
HOSTNAME=$(hostname)

#mail client
MAIL=/usr/bin/mail

	if [ $DISK_UTIL => 95% ]; 
	then
		
		
                DATE_LOGS=`find /var/logs/ -type f -mtime +5`
		FILE_COUNT=`$DATE_LOGS  | wc -l`
		FILE_SIZE=`$DATE_LOGS | wc -c`

		#FILE_SIZE=`$DATE_LOGS |  
		EMAIL="$(date): Files have been deleted on $HOSTNAME that are older ther 5 days old, quantity  of file that have been deleted $FILE_COUNT and the size of the files are $FILE_SIZE"
	
		find /var/logs/ -type f -mtime +5 -exec rm -- {} \; 
	fi

```

---

### Post by cariboo on 2010-02-23
You may get better help here.

---

