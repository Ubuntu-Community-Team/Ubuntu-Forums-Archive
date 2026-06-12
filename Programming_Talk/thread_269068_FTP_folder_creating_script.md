---
title: "FTP folder creating script"
date: 2006-10-01
forum: Programming Talk
---

### Post by pod25 on 2006-10-01
This is my first time at writing a small script.
As the subject says, my script when run in terminal will create a ftp users /home/folder/contents , this is done by copying from a skeleton folder I have set up. The users home/folder is created when he/she first logs in which is controlled my a sql database.
I'm more than sure it can be improved, but as I am a novice script writer, I don't how.
It would be better if the script could be called for by proftpd, in other words, when "testuser" first logs in, his /home/testuser folder is created, then proftpd calls for the script then the script does it's job.
Is this possible ? and remember I'm a novice so be kind.
Here is my script :
```

#!/bin/bash
#BEGIN
MYSQL_PATH=/usr/bin
MYSQL_USER=root
MYSQL_PASS=123
MYSQL_DBNAME=USER_DATABASE_NAME

FTP_HOMEDIRS="/home/FTP"
HOME_TEMPLATE="/etc/skel"

# This should prolly be changed -
SECURITY_MODE=0750

USERNAME=$1
PASSWORD=""

echo -ne "Password: "
read PASSWORD

$MYSQL_PATH/mysql -u $MYSQL_USER -p$MYSQL_PASS $MYSQL_DBNAME -e "INSERT 
INTO ftpusers(userid, passwd, homedir) VALUES('$USERNAME', 
MD5('$PASSWORD'), '$FTP_HOMEDIRS/$USERNAME')"

cp -R $HOME_TEMPLATE $FTP_HOMEDIRS/$USERNAME
chmod -R $SECURITY_MODE $FTP_HOMEDIRS/$USERNAME

#END

```

---

