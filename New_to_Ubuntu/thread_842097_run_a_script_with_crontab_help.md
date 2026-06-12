---
title: "run a script with crontab help"
date: 2008-06-27
forum: New to Ubuntu
---

### Post by janne5011 on 2008-06-27
I have a script which works if I got to the directory
where it is and click it.Looks like this:

host ftp.somehost
user a-user
passwd ****

FILE:snapshot.jpg
#the file is in same directory as this script.

ftp -n $HOST <<END script
quote user $USER
PUT $FILE
END SCRIPT
exit 0

I can run it with ./ftp.sh when in that folder.

If I run it from a shell from another folder it dont works.
I got a msg says snapshot.jpg no such file or directory

so how can I do the same with crontab? I did crontab -e and 
have in crontab:

*/10 * * * * /home/janne/ftp.sh
what would be correct?

---

### Post by forger on 2008-06-27
that runs the command every 10 minutes?

you could add at the beginning of your .sh script
```
cd /home/janne/
```

Also, I think that "<<END script" should be "<<END SCRIPT"

---

### Post by janne5011 on 2008-06-27
> **forger said:**
> that runs the command every 10 minutes?

you could add at the beginning of your .sh script
```
cd /home/janne/
```

Also, I think that "<<END script" should be "<<END SCRIPT"

Ok I try that when Im home after work today.

its the crontabpath which is wrong maybe its fixed with your suggestion.
Btw the script works with "END script".

Thanks

---

### Post by janne5011 on 2008-06-27
forger big thanks :guitar::) :)

here is right way:

crontab:

SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

*/3 * * * * root /home/janne/spart/ftp.sh
#

ftp script:
#!/bin/sh
cd /home/janne/spart
HOST='ftp.somehost'
USER='a-user'
PASSWD='pass'
FILE='snapshot.jpg'

ftp -n $HOST <<END_SCRIPT
quote USER $USER
quote PASS $PASSWD
put $FILE
quit
END_SCRIPT
exit 0

then I typed:
/etc/init.d/cron restart

what it do

upload file snapshot.jpg each third minute.

---

