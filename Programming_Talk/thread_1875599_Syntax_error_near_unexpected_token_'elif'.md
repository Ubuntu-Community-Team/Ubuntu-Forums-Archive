---
title: "Syntax error near unexpected token 'elif'"
date: 2011-11-05
forum: Programming Talk
---

### Post by Deadlyhugs on 2011-11-05
Hi, my friend and I are working on a private server running on 10.04 and when we run the linux_installer.sh we get the error:

[PHP]linux_installer.sh: line 77: syntax error near unexpected token 'elif'
linux_installer.sh: line 77: '  elif [ "${option}" = "b" ]; then'[/PHP]Here is the original code for the file:

[PHP]    elif [ "${option}" = "b" ]; then

        echo
        rm -rf "${bkpath}/logon_backup.sql"
        rm -rf "${bkpath}/character_backup.sql"
        echo " [Deleting Old Backups] Finished…"

        echo
        mysqldump -h ${server} --user=${user} --port=${port} --password=${pass} ${ldb} > "$bkpath}/logon_backup.sql"
        echo " [Backing Up Logon Database] Finished…"

        mysqldump -h ${server} --user=${user} --port=${port} --password=${pass} ${cdb} > "${bkpath}/character_backup.sql"
        echo " [Backing Up Char Database] Finished…"

        echo
        écho " [Backing Up] Finished…"[/PHP]I've tried searching for answers but all I could find was when people don't have 'then' included in the code after the 'elif' command. Any help will be appreciated. Thanks

---

### Post by ofnuts on 2011-11-05
If "elif" is unexpected the problem is likely before it, not after.

---

### Post by Deadlyhugs on 2011-11-05
Ok, i have posted the entire document on pastebin, it is 157 lines so no too big, thanks for any help

[http://pastebin.com/8U1kNg5J](http://pastebin.com/8U1kNg5J)

---

### Post by gsmanners on 2011-11-05
You have matching "done"s for all your "for"s? I think 61 might be the problem.

---

### Post by ofnuts on 2011-11-05
> **gsmanners said:**
> you have matching "done"s for all your "for"s? I think 61 might be the problem.+1

---

### Post by Deadlyhugs on 2011-11-05
tried that and unfortunately no change...we are trying something different but thanks all

---

### Post by ofnuts on 2011-11-06
> **Deadlyhugs said:**
> tried that and unfortunately no change...we are trying something different but thanks allIf I insert "done" just above line 65 (the one that does* echo " Adding Adding Stored Procedures Complete"'*)(<sic> for the "Adding" stutter) then the syntax error disappears.

---

### Post by Deadlyhugs on 2011-11-06
> **ofnuts**: If I insert "done" just above line 65 (the one that does* echo " Adding Adding Stored Procedures Complete"'*)(<sic> for the "Adding" stutter) then the syntax error disappears.     Thanks for this, however it did not work here either. I got another error when doing that.
```
sh ./SkyFireDB/linux_installer.sh
./SkyFireDB/linux_installer.sh: line 67: syntax error near unexpected token `done'
./SkyFireDB/linux_installer.sh: line 67: `      done'
```before it was:
```
sh ./SkyFireDB/linux_installer.sh
./SkyFireDB/linux_installer.sh: line 44: logo: command not found
 i - Install Clean World Database
 u - Update World Database
 x - Exit Tool

 Enter option:  i


 [Cleaning World DB] Finished...
 Adding Stored Procedures
ls: cannot access ./main_db/procs/*.sql: No such file or directory
 [1/0] import: *.sql
./SkyFireDB/linux_installer.sh: line 64: ./main_db/procs/*.sql: No such file or directory
 Adding Adding Stored Procedures Complete
 Importing world data
ls: cannot access ./main_db/world/*.sql: No such file or directory
 [1/0] import: *.sql
./SkyFireDB/linux_installer.sh: line 74: ./main_db/world/*.sql: No such file or directory

 [Importing] Finished...

 Press any key to continue...
```Any other ideas? We are at our wits end with this and everyone else seems to have no problems. I know we are missing something, just trying to figure out what that something is.

Thanks

[COLOR=Red]PS... Also the term done shows in Red Highlight as if it is linked to nothing at all. This is all being done in terminal window. [/COLOR]

---

### Post by Arndt on 2011-11-06
> **Deadlyhugs said:**
> Thanks for this, however it did not work here either. I got another error when doing that.
```
sh ./SkyFireDB/linux_installer.sh
./SkyFireDB/linux_installer.sh: line 67: syntax error near unexpected token `done'
./SkyFireDB/linux_installer.sh: line 67: `      done'
```before it was:
```
sh ./SkyFireDB/linux_installer.sh
./SkyFireDB/linux_installer.sh: line 44: logo: command not found
 i - Install Clean World Database
 u - Update World Database
 x - Exit Tool

 Enter option:  i


 [Cleaning World DB] Finished...
 Adding Stored Procedures
ls: cannot access ./main_db/procs/*.sql: No such file or directory
 [1/0] import: *.sql
./SkyFireDB/linux_installer.sh: line 64: ./main_db/procs/*.sql: No such file or directory
 Adding Adding Stored Procedures Complete
 Importing world data
ls: cannot access ./main_db/world/*.sql: No such file or directory
 [1/0] import: *.sql
./SkyFireDB/linux_installer.sh: line 74: ./main_db/world/*.sql: No such file or directory

 [Importing] Finished...

 Press any key to continue...
```Any other ideas? We are at our wits end with this and everyone else seems to have no problems. I know we are missing something, just trying to figure out what that something is.

Thanks

[COLOR=Red]PS... Also the term done shows in Red Highlight as if it is linked to nothing at all. This is all being done in terminal window. [/COLOR]

Maybe you should show us the whole code as it looks now.

---

### Post by ofnuts on 2011-11-06
> **Deadlyhugs said:**
> Thanks for this, however it did not work here either. I got another error when doing that.```
sh ./SkyFireDB/linux_installer.sh
./SkyFireDB/linux_installer.sh: line 67: syntax error near unexpected token `done'
./SkyFireDB/linux_installer.sh: line 67: `      done'
```before it was:
[CODE]sh ./SkyFireDB/linux_installer.sh

1) with the correction I indicated, the added "done" ends up on line 65.
2) if you call the shell with "*[FONT=Fixedsys]sh ./SkyFireDB/linux_installer.sh[/FONT]*" it is not executed by bash as intended but by dash. This may or may not explain the problem. Make iti executable and call it directly or at least call it with bash.

---

### Post by Deadlyhugs on 2011-11-06
ofnuts, there is the "done" command on line 65 and if I add a 2nd one to it, there is an error indicated and get a message similar to the last one i posted, just with different line numbers.

Arndt, Here is the full file code.
```

#!/bin/bash
# Modified script from WhyDB
############################################################################
#
#  Tool Configuration
#
#  user - MYSQL username
#  pass - MYSQL password
#  wdb - Your world database
#
############################################################################
user="******"
pass="******"
wdb="world"

############################################################################
#
#  Server configuration, do not edit past this point
#
############################################################################
server="localhost"
port="3306"
devpath="./main_db/world"
procpath="./main_db/procs"
uppath="./world_updates"
bkpath="dump"

############################################################################
#
#  Create a backup folder, if one doesn't exist
#
############################################################################
if [ ! -d "${bkpath}" ]; then
    mkdir "${bkpath}"
    chmod 0755 "${bkpath}"
fi

############################################################################
#
#  Main program
#
############################################################################
until [ "${option}" = "x" ]; do
    logo
    echo " i - Install Clean World Database"
    echo " u - Update World Database"
    echo " x - Exit Tool"
    echo
    read -p " Enter option:  " option
    if [ "${option}" = "i" ]; then

        mysqldump -h ${server} --user=${user} --port=${port} --password=${pass} --add-drop-table --no-data ${wdb} | grep ^DROP | mysql -h ${server} --user=${user} --port=${port} --password=${pass} ${wdb}
        echo

        echo
        echo " [Cleaning World DB] Finished..."
        
        echo " Adding Stored Procedures"
        max=`ls -1 "${procpath}"/*.sql | wc -l`
        e=0
        for table in "${procpath}"/*.sql; do
            e=$((${i}+1))
            echo " [${e}/${max}] import: ${table##*/}"
            mysql -h ${server} --user=${user} --port=${port} --password=${pass} ${wdb} < "${table}"
    done
        echo " Adding Adding Stored Procedures Complete"
    echo " Importing world data"        
        max=`ls -1 "${devpath}"/*.sql | wc -l`
        i=0
        for table in "${devpath}"/*.sql; do
            i=$((${i}+1))
            echo " [${i}/${max}] import: ${table##*/}"
            mysql -h ${server} --user=${user} --port=${port} --password=${pass} ${wdb} < "${table}"
        done

        echo
        echo " [Importing] Finished..."
    elif [ "${option}" = "b" ]; then
        
        echo
        rm -rf "${bkpath}/logon_backup.sql"
        rm -rf "${bkpath}/character_backup.sql"
        echo " [Deleting Old Backups] Finished..."
        
        echo        
        mysqldump -h ${server} --user=${user} --port=${port} --password=${pass} ${ldb} > "${bkpath}/logon_backup.sql"
        echo " [Backing Up Logon Database] Finished..."
        
        mysqldump -h ${server} --user=${user} --port=${port} --password=${pass} ${cdb} > "${bkpath}/character_backup.sql"
        echo " [Backing Up Char Database] Finished..."
        
        echo
        echo " [Backing Up] Finished..."
    elif [ "${option}" = "r" ]; then
        
        echo
        mysqldump -h ${server} --user=${user} --port=${port} --password=${pass} --add-drop-table --no-data ${ldb} | grep ^DROP | mysql -h ${server} --user=${user} --port=${port} --password=${pass} ${ldb}
        echo " [Emptying Logon Database] Finished..."
        
        mysql -h ${server} --user=${user} --port=${port} --password=${pass} ${ldb} < "${bkpath}/logon_backup.sql"
        echo " [Restoring Logon Database From Backup] Finished..."
        
        echo
        mysqldump -h ${server} --user=${user} --port=${port} --password=${pass} --add-drop-table --no-data ${cdb} | grep ^DROP | mysql -h ${server} --user=${user} --port=${port} --password=${pass} ${cdb}
        echo " [Emptying Char Database] Finished..."
        
        mysql -h ${server} --user=${user} --port=${port} --password=${pass} ${cdb} < "${bkpath}/character_backup.sql"
        echo " [Restoring Char Database From Backup] Finished..."
        
        echo
        echo " [Restoring Backup] Finished..."

    elif [ "${option}" = "u" ]; then
        
        available_changesets=("${uppath}/changeset_"*.sql)
        if [ "${available_changesets}" != "${uppath}/changeset_*.sql" ]; then

            echo
            echo " Here's a list of available updates:"
            echo
            for changeset in ${available_changesets[@]};
                do
                    echo " ${changeset##*/}"
                done
                
            echo
            read -p " Which update would you like to import (type x to abort):  " index
            if [ "${index}" != "x" ]; then
                update="${uppath}/changeset_${index}.sql"
                if [ ! -f "${update}" ]; then
                    echo
                    echo " ${update} file does not exist."
                else
                    echo
                    echo " Importing changeset ${index}."
                    mysql -h ${server} --user=${user} --port=${port} --password=${pass} ${wdb} < "${update}"
                    echo
                    echo " [Updating World Database] Finished..."
                fi
            fi
        
        else

            echo
            echo " Currently, no updates are available."

        fi
    elif [ "${option}" != "x" ]; then
        echo
        read -p " Incorrect option '${option}'."
        echo
    fi
    if [ "${option}" != "x" ]; then
        echo
        read -p " Press any key to continue..."
        echo
    fi
done

```

_**[COLOR=Red]For some reason, the script suddenly worked, uncertain what changed, but it worked. Thanks to all that tried to help.[/COLOR]**_

---

### Post by ofnuts on 2011-11-07
> **Deadlyhugs said:**
> ofnuts, there is the "done" command on line 65 and if I add a 2nd one to it, there is an error indicated and get a message similar to the last one i posted, just with different line numbers.

In the code you posted at the beginning of the thread, there is no "done" at line 65 (the "do" at line 61 isn't "closed" properly). Of course since I don't think a file would be published with such a blatant error it could have been an erroneous alteration of the file on your side, and in between you got a fresh version so we are trying to fix a problem that's no longer there.

---

