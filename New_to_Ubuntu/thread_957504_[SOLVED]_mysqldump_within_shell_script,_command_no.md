---
title: "[SOLVED] mysqldump within shell script, command not found"
date: 2008-10-24
forum: New to Ubuntu
---

### Post by batfastad on 2008-10-24
Hi everyone

Just trying to make a simple shell script to dump a MySQL database using the mysqldump command

I've got the command all set:
```
mysqldump --host=localhost --user=USERNAME --pass=PASSWORD --comments --create-options --extended-insert --lock-tables --no-create-db --quick --result-file=FILENAME.sql --set-charset --skip-add-drop-table --verbose --databases DATABASE
```
The bits in upper case are text that I'll change to the valid values.

If I type that command into the command line, then it works perfectly.
However when I copy and paste that into a shell script and run the shell script, it doesn't work. It repeats the whole mysqldump command, including all the options and just says command not found at the end

So I'm thinking, do I need to enclose that command in quotes or something within a shell script to get it to execute?

Thanks, B

---

### Post by Crandom on 2008-10-24
You can use Perl:
```
perl -e 'system("mysqldump --host=localhost --user=USERNAME --pass=PASSWORD --comments --create-options --extended-insert --lock-tables --no-create-db --quick --result-file=FILENAME.sql --set-charset --skip-add-drop-table --verbose --databases DATABASE");'
```
At least I remember something like that from when I was programming using perl.

This could be wrong. But I can't delete the post.

---

### Post by batfastad on 2008-10-24
Ok I was using nano to edit the file and it seems it keeps breaking the command onto multiple lines.

In shell scripting, is there anything I need to be aware of or anything I can do to make editing multi-line commands easier?

Break the command into multiple variables, then concatenate them or something?

Sorry for the questions, I'm just trying to get used to the basic syntax of shell scripting

Thanks, B

---

### Post by porchrat on 2008-10-24
> **batfastad said:**
> Hi everyone

Just trying to make a simple shell script to dump a MySQL database using the mysqldump command

I've got the command all set:
```
mysqldump --host=localhost --user=USERNAME --pass=PASSWORD --comments --create-options --extended-insert --lock-tables --no-create-db --quick --result-file=FILENAME.sql --set-charset --skip-add-drop-table --verbose --databases DATABASE
```
The bits in upper case are text that I'll change to the valid values.

If I type that command into the command line, then it works perfectly.
However when I copy and paste that into a shell script and run the shell script, it doesn't work. It repeats the whole mysqldump command, including all the options and just says command not found at the end

So I'm thinking, do I need to enclose that command in quotes or something within a shell script to get it to execute?

Thanks, B

Try running the script with --user=mysql

---

### Post by Sarmacid on 2008-10-24
You can try
```
mysqldump -option1=1 \
-option2=2 \
-option3=3
```

---

### Post by porchrat on 2008-10-24
> **batfastad said:**
> Ok I was using nano to edit the file and it seems it keeps breaking the command onto multiple lines.

In shell scripting, is there anything I need to be aware of or anything I can do to make editing multi-line commands easier?

Break the command into multiple variables, then concatenate them or something?

Sorry for the questions, I'm just trying to get used to the basic syntax of shell scripting

Thanks, B

use "bash -c" to execute as a string...will stop it being broken into multiple lines

---

### Post by batfastad on 2008-10-24
> **Sarmacid said:**
> You can try
```
mysqldump -option1=1 \
-option2=2 \
-option3=3
```

Perfect!
I can see myself using that syntax quite a bit!

Thanks for all the help! :D

---

### Post by kat_ams on 2010-01-23
This is the way my company solved the mysqldump in a shell script:

```

#!/bin/bash
#Script to make a regular copy of a mysql database and gzip it into the SAVEDIR.

USER="*authorized_user*"
PASSWORD="*the_password*"
DATABASE="*database_name*"
SAVEDIR="/backup"

/usr/bin/nice -n 19 /usr/bin/mysqldump -u $USER --password=$PASSWORD --default-character-set=utf8 $DATABASE -c | /usr/bin/nice -n 19 /bin/gzip -9 > $SAVEDIR/$DATABASE-$(date '+%Y%m%d-%H').sql.gz
```

edit the varibles, save it as .bkup.sh and run it in a crontab, then you have an automatic mysql backup.

full explaination of the code in the next post

---

### Post by kat_ams on 2010-01-23
Here is a full code explaination of .bkup.sh

because it's easy to just copy and paste a code, but it's nice to know what the code is doing so you can use pieces in other scripts.


**instructs which shell (command line interpreter) to use (in the example it's the Bourne Again Shell)**
```
#!/bin/bash
```

**a comment line to say what we are going to do. Comments are marked with a # in front of each line**
```

#Script to make a regular copy of a mysql database and gzip it into the SAVEDIR.
```

[SIZE="3"]**This section is where we set the variables to be used again in the script**[/SIZE]

[B]sets a variable named USER, which you set to the user who is authorized to perform mysqldump.
[/B]```
USER="authorized_user"
```

[B]the password of the mysqluser who is allowed to perform a mysqldump
[/B]```
PASSWORD="the_password"
```
[B]
the name of the database you would like to dump[/B]
```
DATABASE="database_name"
```

[B]the directory where you would like to save the backups
[/B]
```
SAVEDIR="/backup"
```

[B]tells the computer to play nice by letting all other processes use the processor before it gets a go. This will keep the backup from causing system slowdown.
[/B]
```
/usr/bin/nice -n 19
``` 

[B]runs the program mysqldump
[/B]```
/usr/bin/mysqldump
```
[B]uses the variables that we set earlier for the user and password to provide username and password to mysqldump.
[/B]```
 -u $USER --password=$PASSWORD
```
[B]Sets the default charachter set of the dumped database to UTF8 (unicode language independant), 
[/B]```
 --default-character-set=utf8
```
[B]uses the databasename from the variables above to tell mysqldump which database to use 
[/B]```
 $DATABASE
```
[B](-c switch) writes to the output file complete insert statements that include the column names. so you can restore the database easily
[/B]```
 -c
```


[B]the | means use the output of the first command for the second comand.
[/B]```
 | 
```
[B]nice this time keeps gzip friendly to the system resources
[/B]```
/usr/bin/nice -n 19
```

[B]squishes the file into a gzip archive with compression level 9 (highest)
[/B]```
/bin/gzip -9
``` 

[B]the > means write the output to a file
[/B]```
>
``` 
[B]
the directory and file name are made from variables we set in the beginning.[/B]
```
$SAVEDIR/$DATABASE-
```

[B]part of the file name is a unique date in the ISO format plus the hour of day. (our backup runs once an hour during opening times so we like to know which hour the backup was made)
[/B]
```
$(date '+%Y%m%d-%H')
```
[B]and of course the file extension .sql (the file is just sql statements) 
[/B]```
.sql
```
[B]and .gz (to tell us that it's squished i.e. compressed into a gzip archive)
[/B]```
.gz
```

that's all there is to it. :D
enjoy scripting

---

