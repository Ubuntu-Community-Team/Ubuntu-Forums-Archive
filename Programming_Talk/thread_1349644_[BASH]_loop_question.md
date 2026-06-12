---
title: "[BASH] loop question"
date: 2009-12-08
forum: Programming Talk
---

### Post by mess110 on 2009-12-08
Hello everyone.

I am writing a little script to help monitor the internet traffic I use through my broadband internet. (i hate 20gb bandwidth and at the end of the month sucky internet)

```

#!/bin/bash

# by Cristian Mircea Messel
# mess110@gmail.com
# http://www.welcome-to-the-world.com
# work in progress...

USER=youruser
PASS=yourpassword
DB=monkitor
INTERFACE=ppp0

#get the ip the interface uses
IP=`ifconfig $INTERFACE| grep 'inet addr:' | cut -d: -f2 | awk '{ print $1}'`
#get the trafic used this session
TRAFFIC=`ifconfig $INTERFACE | grep "RX bytes:"`

#parse download amount this session
DOWNLOAD=${TRAFFIC#* (}
DOWNLOAD=${DOWNLOAD%% *}

#parse upload amount this session
UPLOAD=${TRAFFIC##* (}
UPLOAD=${UPLOAD% *}

#get the date
TIME=`date '+%Y%m%d'`

#check weather there is an entry on a specific date with a specific ip
QUERY=`echo "SELECT time FROM monkitor WHERE time = $TIME AND ip = '$IP'" | mysql -u root --password=bed4love monkitor`
length2=${#QUERY}

if [ $length2 = 0 ]; then
	echo "INSERT INTO monkitor VALUES ('','$IP',$DOWNLOAD,$UPLOAD,$TIME);" | mysql -u $USER --password=$PASS $DB
else
	echo "UPDATE  monkitor SET  download =  '$DOWNLOAD', upload =  '$UPLOAD' WHERE  time = $TIME" | mysql -u $USER --password=$PASS $DB
fi

return 0


```

at the moment I am not interested in optimizing the procedure. What I would like to know on the other hand is how to loop run this script. This makes an update in my database and I want to run this script every.. let's say 5 minutes. I could put a sleep at the end of the script than call the script again. But that does not seem the best way to do it.

How would one normally approach this issue?

Thank you
Cristian

---

### Post by lackoblacko on 2009-12-08
look up cron jobs

---

### Post by mess110 on 2009-12-08
I do have to admit I did think twice before I googled cron job.

but that was part of the funny bone..

Thank you very much. That is a really good solution.

---

### Post by Barriehie on 2009-12-08
If I was going to cron it every 5 minutes then I'ld run it from a RAM drive.  Edit the entry according to your needs!

In fstab:
```

#
# Mount the RamDisk
#
tmpfs /media/ramdisk tmpfs size=64M,nr_inodes=10k,mode=777 0 0

```

Barrie

---

### Post by -grubby on 2009-12-08
There are programs out there that will do this... if I remember it, I'll tell you one.

---

