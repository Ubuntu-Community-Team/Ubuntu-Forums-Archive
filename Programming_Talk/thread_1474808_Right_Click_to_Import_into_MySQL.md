---
title: "Right Click to Import into MySQL"
date: 2010-05-06
forum: Programming Talk
---

### Post by kbrill on 2010-05-06
I import data into MySQL over and over again.  Always from .sql scripts.  I have tried over and over to come up with a script that will

[LIST=1]
[*]Ask for a database name
[*]Sign into MySQL
[*]Drop the Database named in step 1
[*]Create a new database as named in step 1
[*]Import the file I right-clicked on (like source /home/me/Desktop/database.sql)
[/LIST]

Any help would be appreciated.

---

### Post by bapoumba on 2010-05-06
Moved to PT.

---

### Post by kbrill on 2010-05-06
After I posted that question I found my mistake and now have a working script.

Here it is for anyone who cares.

```

#!/bin/bash
# Get domain name
_zenity="/usr/bin/zenity"
_out="/tmp/whois.output.$$"
database=$(${_zenity} --title  "Enter Database Name" \
                    --entry --text "Enter the name of the Database you want this data imported into." )
 
if [ $? -eq 0 ]
then
  # Import into the database
echo "DROP DATABASE IF EXISTS $database;CREATE DATABASE $database;USE $database;" > /home/ken/tmp.sql
notify-send -t 2000 -i gtk-dialog-info "Preparing to Import Database: $database"
mysql -u root -ppassword -h localhost < /home/ken/tmp.sql
notify-send -t 5000 -i gtk-dialog-info "Starting Import to Database: $database"
mysql -v -u root -ppassword -h localhost $database < $1 | tee >(zenity --progress --pulsate --auto-close --auto-kill) > ~/mysql_import.txt

notify-send  -t 10000 -i gtk-dialog-info "Finished Import to Database: $database"

else
  ${_zenity} --error \
             --text="No input provided"
fi


```

---

