---
title: "Bash database backup script - problem"
date: 2018-09-20
forum: Programming Talk
---

### Post by poliman-pl on 2018-09-20
I have a script:
```

#!/bin/bash


#create /root/.my.cnf and add:
#[mysqldump]
#user=root
#password=PASSWORD
#remove the password and user for mysqldump from script
#Wtedy nie b&#281;dzie warningów w konsoli




DATE=$(date +"%d-%m-%Y")
DIRECTORY="/var/www/biosfera.it/home/biosfera_sh/backups"
MYSQLDUMP=/usr/bin/mysqldump
     
#need create .password file in proper directory contains data in form -> user,password
MYSQL_USER="`awk 'BEGIN {FS=","} {print $1}' /root/.credentials`"
MYSQL_PASSWORD="`awk 'BEGIN {FS=","} {print $2}' /root/.credentials`"


#file will be stored in this place
cd $DIRECTORY


#backup the database, each in own file
databases=$(mysql --user=$MYSQL_USER -p$MYSQL_PASSWORD -e "SHOW DATABASES;" | grep -E 'biosfera_base1|biosfera_base2')
for database in $databases
do 
   echo -e "\e[38;5;40mI am doing backup of $database.\e[39m"
   $MYSQLDUMP --force --log-error=error_file.log --user=$MYSQL_USER -p$MYSQL_PASSWORD --databases $database > $database.sql
done


#here need to archive and compress each file
echo  -e "\e[38;5;45mNow I am going to create zipped archives to save some  disk space and remove not necessary files. Please, give me a moment.  :)\e[39m"
 
db="*.sql"
 
for archive in $db
do
    tar -czvf $archive.tar.gz $archive >/dev/null 2>&1
   /bin/mv $archive.tar.gz $archive"_"$DATE.tar.gz
done
 
#make the backup files readable only by root
/bin/chmod 600 *.tar.gz


#delete unnecessary dumped db files
rm *.sql
 
echo
echo "Open path $DIRECTORY to see details."
 
#mail admin that all went properly
echo  "All databases from server $(hostname -f) became backuped. You can  check the log file attached to message." | mutt -s "Report - backup from  day $(date +%y-%m-%d-%H:%M:%S)" backupdb@pol.it -a  "$DIRECTORY/error_file.log"


echo
echo -e "\e[38;5;45mFinished doing databases backup.\e[39m"

```


In  line ```
$MYSQLDUMP --force --log-error=error_file.log  --user=$MYSQL_USER -p$MYSQL_PASSWORD --databases $database >  $database.sql
``` after add $database"-"$DATE.sql (except finishing  $database.sql) files are not created. I tried few ways like  $database$DATE.sql, ${database}-${DATE} and few more. Nothing works (for  testing purposes I commented out archiving loop and removing .sql  files). I just want create filename using the name of specific database  and date. Of course I tried this same in archive loop. Without success.
As  you can see in above script I finally added --> ```
/bin/mv  $archive.tar.gz $archive"_"$DATE.tar.gz
``` in loop which does this  job. But I am curious why above ways don't work.


PS
Is it possible to suppress showing mysql warning about user/pass in above script?

---

### Post by TheFu on 2018-09-20
Why make it complicated?
```
    tar -czvf $archive-$DATE.tar.gz $archive >/dev/null 2>&1
```

I would have the date made from this: date "+%F"  --- YYYY-MM-DD sorts better in a shell.

Here's mine
```
#!/bin/bash
DB_NAME=redmine_default
BACKDIR=/root/backup/

/usr/bin/mysqldump -u root \
    -p`cat ~root/bin/$DB_NAME.passwd.root` $DB_NAME | \
    gzip > $BACKDIR/${DB_NAME}_$((date "+%F")).gz
# Clean up old backups (over 60days since last access)
/usr/bin/find  $BACKDIR -type f -name $DB_NAME\* -atime 60 -delete

```
The script can be run from any PWD. It doesn't care. Using cd and expecting it to work is a failure.  I also try to avoid file  globbing that isn't necessary, since it can have unpredictable results.

There is a security issue putting the DB password on the command line, but for the 3 min the dump requires on a system with no logged users, it wasn't worth figuring out how to do it cleaner.

---

### Post by poliman-pl on 2018-09-21
I have fixed my code:
```

#!/bin/bash

#functions which gives colors
Info () {
        echo -e "\e[1;34m$1\e[0m"
}

Success () {
        echo -e "\e[1;32m$1\e[0m"
}

Important () {
        echo -e "\e[1;33m$1\e[0m"
}

DATE=$(date +"%d-%m-%Y")
DIRECTORY="/var/www/klub-biosfera.pl/home/biosfera_sh/backups"
MYSQLDUMP=/usr/bin/mysqldump

#files will be stored in this place
cd $DIRECTORY

#backup the database, each in own file
databases=$(mysql -e "SHOW DATABASES;" | grep -E 'biosfera_base1|biosfera_base2')
for database in $databases
do
        Info "I am doing backup of \e[4m$database\e[24m."
        echo
        $MYSQLDUMP --force --log-error=error_file.log --databases $database > $database"_"$DATE.sql

        #here need to archive and compress each file
        Important "Now I am going to create zipped archives to save some disk space and remove not necessary files. Please, give me a moment. Working on \e[4m$database\e[24m. :)"
        echo
        tar -czvf $database"_"$DATE.sql.tar.gz $database"_"$DATE.sql >/dev/null 2>&1
done

#make the backup files readable only by root
/bin/chmod 600 *.tar.gz

#delete unnecessary dumped db files
rm *.sql

Info "Open path $DIRECTORY to see details."

#mail admin that all went properly
echo "All databases from server $(hostname -f) became backuped. You can check the log file attached to message." | mutt -s "Report - backup from day $(date +%y-%m-%d-%H:%M:%S)" backupdb@poli.li -a "$DIRECTORY/error_file.log"

echo
Success "Finished doing databases backup."

```

and I have added user/password to /root/.my.cnf file in two sections: [client] and [mysqldump]. Now script does not produce warnings and works like it should. Of course this is now the (working) base to optimizing the code. ;)

---

### Post by SeijiSensei on 2018-09-21
You might be interested in the script I posted here a couple of years back:

[https://ubuntuforums.org/showthread.php?t=2195496&p=12882235&viewfull=1#post12882235](https://ubuntuforums.org/showthread.php?t=2195496&p=12882235&viewfull=1#post12882235)

This maintains a rotation of eight days and archives one backup on the fifteen of each month.

---

